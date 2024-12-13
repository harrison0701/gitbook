# ELK

[https://hackmd.io/@CHW/S1vy8V8ca?utm\_source=preview-mode\&utm\_medium=rec#Elastic-stackELK-安裝-on-docker-一鍵安裝](https://hackmd.io/@CHW/S1vy8V8ca?utm_source=preview-mode\&utm_medium=rec#Elastic-stackELK-%E5%AE%89%E8%A3%9D-on-docker-%E4%B8%80%E9%8D%B5%E5%AE%89%E8%A3%9D)

常用指令

```powershell
# Welcome to the Dev Tools Console!
#
# You can use Console to explore the Elasticsearch API. See the Elasticsearch API reference to learn more:
# https://www.elastic.co/guide/en/elasticsearch/reference/current/rest-apis.html
#
# Here are a few examples to get you started.

# Create an index
PUT /my-index

# Add a document to my-index
POST /my-index/_doc
{
    "id": "park_rocky-mountain",
    "title": "Rocky Mountain",
    "description": "Bisected north to south by the Continental Divide, this portion of the Rockies has ecosystems varying from over 150 riparian lakes to montane and subalpine forests to treeless alpine tundra."
}

# Perform a search in my-index
GET /my-index/_search?q="rocky mountain"

#檢查ip位置
GET /_cat/nodes?v

#查看叢集內的索引。
GET /_cat/indices?v

#Primary Shard
 GET /_cat/indices?v&expand_wildcards=all
 
 #建立一個user索引
 PUT /users
 
 #查看所有index
 GET /_cat/indices?v
 
 GET /_cat/shards?v
 
 #健康檢查
 GET /_cluster/health
 
 #刪除index
 DELETE /my-index  

 GET /_cat/nodes?v

 #指定新增(指定分片數量)
 PUT /products
 {
  "settings": {
    "number_of_shards": 1,
    "number_of_replicas": 1
  }
 }

 #新增產品文件
 POST /products/_doc
 {
  "name": "Coffee Maker",
  "price": 64,
  "in_stock":10
 }

#更新id為_100的文件
PUT /products/_doc/100
{
  "name": "Toaster",
  "price":79,
  "in_stock":4
}

#取得id為_100的文件
GET /products/_doc/100

#更新id為_100的文件的存貨
POST /products/_update/100
{
 "doc": {
   "in_stock": 6
  }
}

#新增tag
POST /products/_update/100
{
 "doc": {
   "tags": ["electronics"]
  }
}

#修改產品的數量(使用腳本)
post /products/_update/100
{
  "script" : {
    "source": "ctx._source.in_stock--"
  }
}

#修改產品的數量(使用腳本)
post /products/_update/100
{
  "script" : {
    "source": "ctx._source.in_stock-=params.quanity",
    "params": {
      "quanity": 4
    }
  }
}
 
 #更新插入(in_stock++)
 POST /products/_update/101
 {
   "script": {
     "source": "ctx._source.in_stock++"
   },
   "upsert": {
     "name": "Blender",
     "price": 399,
     "in_stock" : 5
   }
 }
 
 GET /products/_doc/101
 
 #刪除
 DELETE /products/_doc/101
 
 #處理併發問題
 GET /products/_doc/100
 
 POST /products/_update/100?if_primary_term=2&if_seq_no=17
 {
   "doc": {
     "in_stock": 123
   }
 }
 
 
```
