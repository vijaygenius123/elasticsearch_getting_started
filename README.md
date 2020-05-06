# elasticsearch_getting_started

## Running On Docker

docker run -p 9200:9200 -p 9300:9300 --name elasticsearch -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.6.2


## Basic Commands

1. Check If ES Is Up

```bash
curl -XGET http://localhost:9200
```
Should Output
```bash
{
  "name" : "89ac8d17eba6",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "pWyKiVrcSI6ksy58dCyLvA",
  "version" : {
    "number" : "7.6.2",
    "build_flavor" : "default",
    "build_type" : "docker",
    "build_hash" : "ef48eb35cf30adf4db14086e8aabd07ef6fb113f",
    "build_date" : "2020-03-26T06:34:37.794943Z",
    "build_snapshot" : false,
    "lucene_version" : "8.4.0",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}
```

2. Check Health

```bash
curl -XGET 'http://localhost:9200/_cat/health?v&pretty'
```
Should Output
```bash
poch      timestamp cluster        status node.total node.data shards pri relo init unassign pending_tasks max_task_wait_time active_shards_percent
1588750495 07:34:55  docker-cluster green           1         1      0   0    0    0        0             0                  -                100.0%
```

3. Get indices

```bash
curl -XGET 'http://localhost:9200/_cat/indices?v&pretty'
```

4. Get Nodes
```bash
curl -XGET 'http://localhost:9200/_cat/nodes?v&pretty'
```


5. Create Index 
```bash
curl -XPUT 'http://localhost:9200/products?pretty'
```

Output 
```bash
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "products"
}
```