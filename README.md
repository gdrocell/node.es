# Installing

You can clone the repo with the following

```bash
	git clone https://github.com/gdrocell/node.es.git
```

Then, in the root of the repository, run the following...

```bash
	npm install
```

# Configuration

The proxy configuration now has some more variables including proxyClientProtocol and esThriftServerSeeds.  Following is a sample
proxy configuration... 

```json
{
    "seeds" : ["localhost:9200"],
    "refresh" : 2000,
    "allow" : {
        "GET" : ["(_search|_status|_mapping|_count|_hello)","/.+/.+/.+/_mlt","/.+/.+/.+]"],
        "POST" : ["_search|_count","/.+/.+/.+/_mlt"],
        "OPTIONS" : [".*"]
    },
    "port" : 8124,
    "host": "127.0.0.1",
    "proxyClientProtocol" : "thrift",
    "esThriftServerSeeds" : [ {
                                "host": "localhost", "port": 9499
                              }
                            ]
}
```

you can set proxyClientProtocol to "thrift" or "http", and you can add an array of thrift servers using the elastic search thrift
transport plugin.  In the example there is one thrift server specified on localhost with port 9499.  Note: the default port of the
thrift server for the elasticsearch plugin is 9500. 

You can also set the ezbake configuration directory with the following command line

```bash
	export EZCONFIGURATION_DIR=path/to/ezbake config dir
```

Setting thrift.use.ssl=true will have the proxy use SSL if you also have set the proxyClientProtocol to thrift.

# Sample Proxy



