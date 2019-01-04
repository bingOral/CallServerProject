# ImportDataToElasticRearchProject

### 1.import data to elasticSearch
- a.English Data structure
```
{
    "mappings":{
        "data":{
            "properties":{
                "wavname":{
                    "type":"keyword"
                },
                "origin_audio":{
                    "type":"keyword"
                },
                "url":{
                    "type":"keyword"
                },
                "info":{
                    "type":"text"
                },
                "length":{
                    "type":"float"
                },
                "oral_score":{
                    "type":"float"
                },
                "first_asr_text":{
                    "type":"keyword"
                },
                "first_align_text":{
                    "type":"keyword"
                },
                "first_text_similarity":{
                    "type":"float"
                },
                "second_asr_text":{
                    "type":"keyword"
                },
                "second_align_text":{
                    "type":"keyword"
                },
                "second_text_similarity":{
                    "type":"float"
                },
                "third_asr_text":{
                    "type":"keyword"
                },
                "third_align_text":{
                    "type":"keyword"
                },
                "third_text_similarity":{
                    "type":"float"
                },
                "forth_asr_text":{
                    "type":"keyword"
                },
                "forth_align_text":{
                    "type":"keyword"
                },
                "forth_text_similarity":{
                    "type":"float"
                },
                "first_reserved":{
                    "type":"float"
                },
                "second_reserved":{
                    "type":"keyword"
                },
                "third_reserved":{
                    "type":"text"
                },
                "flag":{
                    "type":"text"
                },
                "time":{
                    "type":"date",
                    "format":"yyy-MM-dd HH:mm:ss"
                }
            }
        }
    }
}
```
- b.Nuance Data structure
```
{
    "mappings" : {
      "data" : {
        "properties" : {
          "length" : {
            "type" : "float"
          },
          "reference" : {
            "type" : "keyword"
          },
          "server" : {
            "type" : "keyword"
          },
          "text" : {
            "type" : "keyword"
          },
          "wavname" : {
            "type" : "keyword"
          }
        }
      }
    }
  }
}

```

### 2.Userful query
- a.查询音频总时长：
```
GET /callserv_edu_oral_en/data/_search
{
  "size": 0,
  "aggs": {
    "SUM_LENGTH": {
      "sum": {
        "field": "length"
      }
    }
  }
}
```
- b.查询爬取哪些URL数据：
```
GET /callserv_data_english/data/_search
{
  "_source": false, 
  "size": 0, 
  "aggs": {
    "distinct": {
      "cardinality": {
        "field": "url"
      }
    }
  }
}
```

