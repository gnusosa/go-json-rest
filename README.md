
Go-Json-Rest
============

*A quick and easy way to setup a RESTful JSON API*

[![Build Status](https://travis-ci.org/ant0ine/go-json-rest.png?branch=master)](https://travis-ci.org/ant0ine/go-json-rest)

**Go-Json-Rest** is a thin layer on top of `net/http` that helps building RESTful JSON APIs easily. It provides fast URL routing using [Go-UrlRouter](https://github.com/ant0ine/go-urlrouter), and helpers to deal with JSON requests and responses. It is not a high-level REST framework that transparently maps HTTP requests to procedure calls, on the opposite, you constantly have access to the underlying
`net/http` objects.

Install
-------

This package is "go-gettable", just do:

    go get github.com/ant0ine/go-json-rest

Example
-------

	package main
	import (
	        "github.com/ant0ine/go-json-rest"
	        "net/http"
	)
	type User struct {
	        Id   string
	        Name string
	}
	func GetUser(w *rest.ResponseWriter, req *rest.Request) {
	        user := User{
	                Id:   req.PathParam("id"),
	                Name: "Antoine",
	        }
	        w.WriteJson(&user)
	}
	func main() {
	        handler := ResourceHandler{}
	        handler.SetRoutes(
	                rest.Route{"GET", "/users/:id", GetUser},
	        )
	        http.ListenAndServe(":8080", &handler)
	}


More Examples
-------------

- [Countries](https://github.com/ant0ine/go-json-rest/blob/master/examples/countries.go) Demo very simple GET, POST, DELETE operations
- [Users](https://github.com/ant0ine/go-json-rest/blob/master/examples/users.go) Demo the mapping to object methods
- [SPDY](https://github.com/ant0ine/go-json-rest/blob/master/examples/spdy.go) Demo SPDY using github.com/shykes/spdy-go


Documentation
-------------

- [Online Documentation (godoc.org)](http://godoc.org/github.com/ant0ine/go-json-rest)


Copyright (c) 2013 Antoine Imbert

[MIT License](https://github.com/ant0ine/go-json-rest/blob/master/LICENSE)


