Case
-------------------------------

1. Join ElasticSearch Network

    - Password: ElasticSearch
    
2. Unzip elasticsearch

3. Start elastic search

    - Mac / Linux: bin/elasticsearch -f
    - Windows: bin/elasticsearch


Create index for holding banking transactions
-------------------------------

# 1. Having more *shards* enhances the _indexing_ performance and allows to
#    _distribute_ a big index across machines.
# 2. Having more *replicas* enhances the _search_ performance and improves the
#    cluster _availability_.


    curl -XPUT 'http://localhost:9200/banking' -d '{
        "settings" : {
            "number_of_shards" : ?,
            "number_of_replicas" : ?
        }
    }'


Bulk insert banking transactions
-------------------------------

    curl -s -XPOST localhost:9200/_bulk --data-binary @transer_m.txt; echo


Count number of transactions for account number 13816695547
-------------------------------

    curl -XGET 'http://localhost:9200/banking/transaksjoner/_count?q=accountNumber:13816695547'


Find average transaction amount
-------------------------------

    curl -XPOST 'http://localhost:9200/banking/transaksjoner/_search?pretty=true' -d '{
        "query" : {
            "match_all" : {}
        },
        "facets" : {
            "stat1" : {
                "statistical" : {
                    "field" : "amount"
                }
            }
        }
    }'


Find average transaction amount for account number 13816695547
-------------------------------

    curl -XPOST 'http://localhost:9200/banking/transaksjoner/_search?pretty=true' -d '{
        "query" : {
	            "term" : { "accountNumber" : "13816695547" }
	    },
        "facets" : {
            "stat1" : {
                "statistical" : {
                    "field" : "amount"
                }
            }
        }
    }'


Stop some nodes
-------------------------------



Delete index
-------------------------------

    curl -XDELETE http://localhost:9200/banking
