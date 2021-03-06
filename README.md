go-jaeger-plugin
==================

Allows usage of Jaeger Bindings for Go OpenTracing API
For more information on Jaeger - https://github.com/jaegertracing/jaeger-client-go

## Setup

* NOTE: As of [2017.08.09](https://golang.org/pkg/plugin/) the plugins lib
in Go only works in Linux.

Build the plugin:

```
$ cd plugin
```

```
$ make
```

## Installing

Make plugin executable:

```
$ chmod +x jaeger-plugin.so
```

Copy the plugin to ./ipfs:

```
$ cp jaeger-plugin.so $IPFS_PATH/plugins/jaeger-plugin.so
```

Set the tracer name environment variable
```
$ export IPFS_TRACER_NAME=$(ipfs id | jq '.ID')
```

## Viewing Traces

Start the [All in One Jaeger UI](https://jaeger.readthedocs.io/en/latest/getting_started/#all-in-one-docker-image) to view the Traces

```
docker run -d -e COLLECTOR_ZIPKIN_HTTP_PORT=9411 -p5775:5775/udp -p6831:6831/udp -p6832:6832/udp \
  -p5778:5778 -p16686:16686 -p14268:14268 -p9411:9411 jaegertracing/all-in-one:latest
```

Open `localhost:16686` in browser.

For more information on getting started with Jaeger UI
- https://jaeger.readthedocs.io/en/latest/getting_started/

### I don't have linux but I want to do this somehow!

As stated above, the plugin library only works in Linux. Bug the go team to
support your system!

* Or use a linux virtualbox, and mount this directory.
