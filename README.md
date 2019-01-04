# CallServer数据项目

### 一、项目介绍：
- 抓取和整理网络音频数据，为CallServer项目优化数据模型提供数据支撑；


### 二、工作流程：
![](数据团队、教研团队工作流程.png)


### 三、子项目介绍：
#### 1.[爬虫项目](https://github.com/bingOral/CrawlDataProject)
#### 2.[切割音频项目](https://github.com/bingOral/CutAudioProject)
#### 3.[调取外部ASR项目](https://github.com/bingOral/ProcessWavProject)
#### 4.[文本对齐项目](https://github.com/bingOral/AlignTextProject)
#### 5.[Oral提取项目](https://github.com/bingOral/ParserEduCSVDataProject)
#### 6.[Logstash导出项目](https://github.com/bingOral/ExportDataFromElasticProject)


### 四、elasticSearch表结构
- 1.English Data结构
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
- 2.Nuance Data结构
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


### 五、Userful query
- 1.查询音频总时长：
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
- 2.查询爬取哪些URL数据：
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

- 欢迎补充！！！


#### 六、其他支持：
- 1.[科学上网代理池](https://github.com/bingOral/haipproxy)



