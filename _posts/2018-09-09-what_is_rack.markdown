---
layout: post
title:      "What is Rack"
date:       2018-09-10 01:10:02 +0000
permalink:  what_is_rack
---


Rack sits between your code and the web server to deal with how Ruby should be able to respond to HTTP requests. 

* It checks if the HTTP Request is well formed
* It receives the request and then passes it to a ruby method/application
* It acts as an interface for how Ruby can speak HTTP
* It will take Ruby and translate it back to HTTP

It is a standard interface between HTTP and Ruby. It provides an adapter on one end to Ruby code and on the other end an adapter to any HTTP server

Rack Apps are Ruby objects that respond to only one method "call" through a single argument and returns a three part array: status code, response header, response body as an array of strings.

More than anything it is a standard by which Ruby apps can interact with the web.
