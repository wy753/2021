# first version
```python
import json
import os
import psycopg2
import urllib3
import boto3

db_host = "apg-dev-imperf-alpha.cluster-czeqb45xpmuo.us-east-2.rds.amazonaws.com"
db_port = 5432
db_name = "alphadb"
db_user = "alphadbuser"
db_pass = "alphaalpha"
db_table = "test.user"

url = "https://acid-bisamws.hosting.factset.com/bisam-ws/rpc/v1/getRunDataExtractTemplate?templateCode=OAZ_02.01_201222&lgCode=en"
headers = {
    'Authorization': 'Basic V1lhbmc6YWJjZDEyMzRA'
}



def make_conn():
    conn = None
    try:
        conn = psycopg2.connect("dbname='%s' user='%s' host='%s' password='%s'" % (db_name, db_user, db_host, db_pass))
    except:
        print("I am unable to connect to the database")
    return conn


def fetch_data(conn, query):
    result = []
    print("Now executing: %s",query)
    cursor = conn.cursor()
    cursor.execute(query)

    raw = cursor.fetchall()
    for line in raw:
        result.append(line)

    return result

def lambda_handler(event, context):
    print('before service call')
    http = urllib3.PoolManager()
    response = http.request('GET', url, headers=headers)
    print(response.status)
    print('after the service call')
    json = response.data
    print(json)
    s3 = boto3.resource("s3")
    s3.Bucket('aci-it-pace-athena-results-66-us-east-2').put_object(Key='lambda/test.json', Body=json)

    record_list = json.load(json)

    sql_string = 'INSERT INTO user  '

    
    conn = make_conn()
    result = fetch_data(conn,"select * from test.user")
    print(result)
    # TODO implement
    return {
        'statusCode': 200,
        'body': 'done'
    }

```