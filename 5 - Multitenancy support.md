Multi tenancy support
-------------------------------

Create two indexes
-------------------------------

    curl -XPUT http://localhost:9200/logs-jan-2013

	curl -XPUT http://localhost:9200/logs-feb-2013 -d \
	'
	index :
	    store:
	        type: memory
	'



PUT some data
-------------------------------

    curl -XPUT http://localhost:9200/logs-jan-2013/entry/1 -d '{
        "date": "2013-01-01T14:12:12",
        "level": "ERROR",
        "message": "Something bad happened"
    }'

    curl -XPUT http://localhost:9200/logs-feb-2013/entry/1 -d '{
        "date": "2013-02-01T14:12:12",
        "level": "ERROR",
        "message": "Something almost as bad happened"
    }'

Query data
-------------------------------

    curl -XGET http://localhost:9200/logs-jan-2013,logs-feb-2013/entry/_search?q=level:ERROR

    curl -XGET http://localhost:9200/_all/entry/_search?q=level:ERROR