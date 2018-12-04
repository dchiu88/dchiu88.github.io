---
layout: post
title:      "Sinatra Project"
date:       2018-09-22 12:36:48 -0400
permalink:  setting_up_sinatra
---


I got a bit lost after my CLI project. There was quite a bit to cover with SQL, ORM, ActiveRecord and Sinatra. I found myself stuck somewhere towards my second to last sinatra exercise and started building my project because I needed to see what I was actually learning.

I needed to build something in a way that was useful to me and at the same time involved a level of creative process. At the same time, I wanted to find a way to address some of the issues I'm facing at work. The result was the creation of Dokumentor. 

Dokumentor is a basic autocomplete webapp where a user can save text that is repeatedly entered into a database and quickly find typing into a form that autocompletes the response. 

It uses Sinatra on the backend CRUD process and HTML5, CSS and Javascript on the front in order to search for previous responses. 

Essentially, the way it works is that it uses Sinatra/Ruby to create a user, and allow that user to save response entries to its database. The entries that belong to the user are stored as an array and is iterated over using Javascript when the user begins typing into the search form. 

The user can then find the entry quickly without needing to retype repetitive text.


