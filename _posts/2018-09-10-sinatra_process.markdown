---
layout: post
title:      "Sinatra Process"
date:       2018-09-11 01:56:57 +0000
permalink:  sinatra_process
---

Part 1 - Create Files and Folders
1. Create Gem file with Bundle Init
2. Create rakefile 
3. Create readme
4. Create config.ru to mount controllers 
5. Create models folder
6. creae views folder
7. create controllers folder
8. Create application_controller.rb file
9. Create config folder
10. Create environment.rb file to require all gems and set up active record connection
11. Create DB folder for migrations
12. Create Migrate folder for migrations in migrations folder

Part 2 - Build Gemfile
1. Require gems: sinatra, activerecord, sinatra-activerecord, rake, sqlite3, thin, shotgun, require_all
2. run bundle install

Part 3- Environment file, Rakefile, Config.ru file
1. Require bundler, Establish connection between Active REcord and SQlite database, Require app directory
2. Require Bundler, bundler.require - requires all default gems in the gemfile
3. Establish connection between ActiveRecord and Database
4. Require app director: require_all "app"

Setup Rakefile
1. require './config/environment'
2. require 'sinatra/activerecord/rake'

Setup Config.ru
1. require './config/environment'
2. if ActiveREcord::Base.connection.migration_context.needs_migration? raise 'Migrations are pending. Run 'rake db:migrate' to resolve this issue."end
3.  mount application controller run APplicationController

Setup Rake File
