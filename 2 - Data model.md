Data model
-------------------------------

Index some data
-------------------------------

                                     
    curl -XPUT http://localhost:9200/twitter/user/landro -d '{
        "name" : "Stefan Landrø"
    }'

    curl -XPUT http://localhost:9200/twitter/tweet/1 -d '{
        "user": "landro",
        "post_date": "2013-03-01T06:00:00",
        "message": "Getting psyched for BEKK fagdag"
    }'

    curl -XPUT http://localhost:9200/twitter/tweet/2 -d '{
        "user": "landro",
        "post_date": "2013-03-01T06:00:01",
        "message": "Even more psyched"
    }'


Check out type-mappings using head console
-------------------------------

[Head console](http://localhost:9200/_plugin/head/)