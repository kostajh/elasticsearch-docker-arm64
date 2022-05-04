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

## Building for a new version of ElasticSearch

1. Clone `elastic/elasticsearch` locally from GitHub
2. Checkout the v6.8.23 (or whatever) tag
3. Run `docker run -v $PWD:/elasticsearch openjdk:11 bash -c "cd /elasticsearch; ./gradlew assemble"` and wait 1.5 hours
4. Upload the distribution file (`distribution/archives/oss-tar/build/distributions/elasticsearch-oss-6.8.23-SNAPSHOT.tar.gz`) to a public place (currently, people.wikimedia.org/~kharlan)
5. Adjust this Dockerfile to refer to the new file
6. `docker build . -t elasticsearch-arm:6.8.23`
