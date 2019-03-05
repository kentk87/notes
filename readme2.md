1. Check Index Size
curl -H'Content-Type: application/json' -XGET 'localhost:9200/_cat/indices?v&s=store.size:desc'

2. Check Cluster Health
curl -H'Content-Type: application/json' -XGET 'localhost:9200/_cluster/health?pretty'

3. Recover red index
curl -H'Content-Type: application/json' -XPOST 'localhost:9200/_cluster/reroute?retry_failed'

4. Update All Settings to Allow Delete

curl -H'Content-Type: application/json' -XPUT 'localhost:9200/_settings' -d'
{
    "index": {
        "blocks": {
            "read_only_allow_delete": "false"
}}}'

5. Update All Setting to Change Replica:
curl -H'Content-Type: application/json' -XPUT 'localhost:9200/_settings' -d'
{
    "index" : {
        "number_of_replicas" : 0
    }
}'
