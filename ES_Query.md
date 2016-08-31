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
