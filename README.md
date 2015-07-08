This container builds on the official elasticsearch image. Currently installing elasticsearch 1.6

## Use

```
docker run ddogs/elasticsearch
```

Optionally you can override specific elasticsearch configuration settings:

```
docker run ddogs/elasticsearch -Des.node.name="awesome_node"
```


Exmaple docker-compose file:

```
elasticsearch:
  image: ddogs/elasticsearch
  hostname: elasticsearch
  privileged: true
  volumes:
    - ./storage:/usr/share/elasticsearch/data
    - ./config:/usr/share/elasticsearch/config
  ports:
    - "9200:9200/tcp" 
    - "9300:9300/tcp" 
```

You can map specific  volumes for your _data_ directory and your own elasticsearch config file


__NOTE__: Privileged is now required, this is because we're setting memlock unlimited to ensure optimum performance of ES.
 
## Logging
By default, only WARN and above will be visible in the stdout and subsequently docker logs.  INFO and above are logged to /storage/logs

## License
This docker application is distributed unter the MIT License (MIT).

Elasticsearch itself is licenced under the [Apache](https://github.com/elastic/elasticsearch/blob/master/LICENSE.txt) License.