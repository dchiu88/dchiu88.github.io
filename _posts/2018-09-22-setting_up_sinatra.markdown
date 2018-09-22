---
layout: post
title:      "Setting up Sinatra "
date:       2018-09-22 16:36:47 +0000
permalink:  setting_up_sinatra
---

1. Include all necessary gems in gemfile
> source "https://rubygems.org"

gem 'activerecord', :require => 'active_record'
gem 'sinatra-activerecord', :require => 'sinatra/activerecord'

gem 'sinatra', require: 'sinatra/base'
gem 'sinatra-reloader', require: false
gem 'shotgun'
gem 'sqlite3'
gem 'rake'
gem 'pry'
gem 'tux'
gem 'require_all'


group :test do
  gem 'rspec'
  gem 'rack-test'
  gem 'capybara'
end

2. Set up environment file
> ENV['SINATRA_ENV'] ||= "development"

require 'bundler'
Bundler.require(:default, ENV['SINATRA_ENV'])

ActiveRecord::Base.establish_connection(
  :adapter => "sqlite3",
  :database => "db/#{ENV['SINATRA_ENV']}.sqlite"
  )

require 'sinatra/base'
require 'sinatra/reloader'

require_all './app'
require_all './app/models'

3. Set up Migrations

Migrations are a way to create and update tables without needing to manually go through SQL. Using the migrations system to apply the schema changes is easier than keeping track of the changes manually and executing them manually at the appropriate time.

4. Set up Models
5. Set up Controller
