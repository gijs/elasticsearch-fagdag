PUT, GET and DELETE data
-------------------------------

PUT some data
-------------------------------

    curl -XPUT http://localhost:9200/twitter/tweet/3 -d '{
        "user": "landro",
        "post_date": "2013-03-01T06:02:00",
        "message": "Oh my, it so easy to GET the data"
    }'


GET some data
-------------------------------

    curl -XGET http://localhost:9200/twitter/tweet/3


DELETE some data
-------------------------------

    curl -XDELETE http://localhost:9200/twitter/tweet/3