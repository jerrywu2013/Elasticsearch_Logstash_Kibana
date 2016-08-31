```
curl 'localhost:9200/_cat/indices?v'
curl -X GET 'http://localhost:9200/python_to_elastic/pyelastic/1?pretty'
curl -X GET 'http://localhost:9200/python_to_elastic/pyelastic/_search?pretty'
```
```
curl -X GET 'http://localhost:9200/python_to_elastic/pyelastic/_search?pretty' -d '
{
    "query" : {
        "match" : {
            "name" : "和平東路三段"
        }
    }
}'
```
