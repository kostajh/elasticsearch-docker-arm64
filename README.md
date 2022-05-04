# ElasticSearch 6.8.23 arm64 docker image

## Building the image
```
docker build . -t elasticsearch-arm:6.8.23
```

## Running the image
To run it:

```
docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e "bootstrap.system_call_filter=false" elasticsearch-arm:6.8.23
```
