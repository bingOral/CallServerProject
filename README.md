# ImportDataToElasticRearchProject

### 1.import data to elasticSearch
>data structure
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

### 2.Userful query
>a. query wavname
