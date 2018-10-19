# REST Layer ElasticSearch Backend

[![godoc](http://img.shields.io/badge/godoc-reference-blue.svg?style=flat)](https://godoc.org/github.com/rs/rest-layer-es) [![license](http://img.shields.io/badge/license-MIT-red.svg?style=flat)](https://raw.githubusercontent.com/rs/rest-layer-es/master/LICENSE) [![build](https://img.shields.io/travis/rs/rest-layer-es.svg?style=flat)](https://travis-ci.org/rs/rest-layer-es) [![GuardRails badge](https://badges.production.guardrails.io/moul/rest-layer-es.svg)](https://www.guardrails.io)

This [REST Layer](https://github.com/rs/rest-layer) resource storage backend stores data in an ElasticSearch cluster using [olivere/elastic](gopkg.in/olivere/elastic.v3).

## Usage

```go
import "github.com/rs/rest-layer-es"
```

Create an [elastic]("gopkg.in/olivere/elastic.v3") client:

```go
client, err := elastic.NewClient()
```

Create a resource storage handler with a given DB/collection:

```go
s := es.NewHandler(client, "index", "type")
```

Use this handler with a resource:

```go
index.Bind("foo", foo, s, resource.DefaultConf)
```

You may want to create as many ElasticSearch handlers with different index and/or type. You can share the same `elastic` client across all you handlers.
