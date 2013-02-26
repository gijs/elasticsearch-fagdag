Searching for data
-------------------------------

Add some more data
-------------------------------

    curl -XPUT http://localhost:9200/twitter/tweet/3 -d '{
        "user": "landro",
        "post_date": "2013-03-01T14:12:12",
        "message": "Rock and roll - searching is easy!"
    }'

Use Lucene-style query
-------------------------------

    curl -XGET http://localhost:9200/twitter/tweet/_search?pretty=true&q=user:landro


Use JSON-style query DSL
-------------------------------

    curl -XGET http://localhost:9200/twitter/tweet/_search?pretty=true -d '{
        "query" : {
            "term" : { "user": "landro" }
        }
    }'


    curl -XGET http://localhost:9200/twitter/_search?pretty=true -d '{
        "query" : {
            "range" : {
                "post_date" : {
                    "from" : "2013-03-01T08:00:00",
                    "to" : "2014-01-01"
                }
            }
        }
    }'