---
layout: post
title:      "Web Frameworks and Sinatra"
date:       2018-09-09 22:13:17 -0400
permalink:  web_frameworks_and_sinatra
---

Building dynamic web applications in any language is a complex job requiring intimate knowledge of hundreds of technologies and specifications. The good news, however, is that many of these requirements are universal and every web application must conform to these standards.

For example, any robust web application will need to handle request routing and provide a mechanism for the application to respond to different URLs with the appropriate response. Even a simple blog application has to handle a request to GET '/posts' to show all the recent blog posts vs a request to GET '/authors' to list all the authors.

Similarly, web applications require the ability to render templates to produce consistently structured dynamic content. A GET request to /posts/1 must render the HTML for the first post just as a request to GET '/posts/2' will render identically structured HTML but with content for the second post. This is possible because of templates.

Web frameworks take all these routine and common requirements of any web application and abstract them into code and patterns that provide these functionalities to your application without requiring you to build them yourself.

Frameworks provide structure and libraries that allow you to focus on your application and not applications in general. The bigger the framework, the more you can rely on it to provide you with common needs. The smaller the framework, the more you'll have to build things yourself.

# Sinatra Intro
Sinatra is a Domain Specific Language implemented in Ruby that's used for writing web applications. Created by Blake Mizerany, Sinatra is Rack-based, which means it can fit into any Rack-based application stack, including Rails. It's used by companies such as Apple, BBC, GitHub, LinkedIn, and more.

Essentially, Sinatra is nothing more than some pre-written methods that we can include in our applications to turn them into Ruby web applications.

Unlike Ruby on Rails, which is a Full Stack Web Development Framework that provides everything needed from front to back, Sinatra is designed to be lightweight and flexible. Sinatra is designed to provide you with the bare minimum requirements and abstractions for building simple and dynamic Ruby web applications.

In addition to being a great tool for certain projects, Sinatra is a great way to get started in web application development with Ruby and will prepare you for learning other larger frameworks, including Rails.

# Sinatra Basics

*config.ru*
This is analogous to a bin file. The purpose of config.ru is to detail to Rack the environment requirements of the application and start the application.

*controller*
config.ru requires a valid Sinatra Controller to run. A Sinatra Controller is simply a ruby class that inherits from Sinatra::Base. This inheritance transforms into a web application by giving it a Rack-compatible interface behind the scenes via the Sinatra framework. 

In a single controller application, a single file defining the controller, like app.rb, will suffice. That controller will define every single URL and response of our application.

Controllers define an HTTP method using the sinatra routing DSL provided by methods like get and post. When you enclose these methods within a ruby class that is a Sinatra Controller, these HTTP routes are scoped and attached to the controller.

The final step in creating a controller is mounting it in config.ru. Mounting a controller means telling Rack that part of your web application is defined within the following class. We do this in config.ru by using run Application where run is the mounting method and Application is the controller class that inherits from Sinatra::Base and is defined in a previously required file.

*Routes*
Routes are the part of an application that connect HTTP requests to a specific method in your application code built to handle responding to such a request (that part of code is called a Controller Action).

Users interact with our application by requesting specific URLs via HTTP. URLs are the interface to a web application.

How does our application know what to show a user based on the web request they sent? Through the routes we program in our application. Being able to draw a route in a web application to respond to an HTTP request is the absolute first step in building anything on the web.

In Sinatra, a route is constructed by pairing an HTTP method/verb, like GET or POST with a URL-matching pattern, i.e. a string that matches what users type in to their browser when they want to visit our webpage. 

Routes match the web request sent by a client to some code in our application that tells the app what data and templates to send back to the client.

*Params*
Params are a hash where user input is stored.
