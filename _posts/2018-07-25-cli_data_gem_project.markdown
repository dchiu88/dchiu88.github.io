---
layout: post
title:      "CLI Data Gem Project"
date:       2018-07-26 00:30:15 +0000
permalink:  cli_data_gem_project
---


I wrote my first program! To be honest I wish it had more pizzazz, but it is exciting to complete. It was honestly less complicated than I originally thought, which is a relief.

There are multiple parts to the program including:

1. Getting the Gem Set Up
2. The environment file
3. The bin file
4.  The CLI
5.  The Object being scraped
6.  The Scraper

# Getting the Gem Set Up
Getting the Gem Set Up is easy with bundler. It really just is bundler gem #name_of_gem

# The environment file
The environment file is where we set up the program so that it can read all the libraries and files required for the program. In this case, since we are scraping, I required nokogiri and open-uri right off the bat. Every time I created a new file I also added that to my environment file.

# The CLI
The CLI is where the magic happens. In a sense it is the point guard because it is the file that brings everything together, but at the same time hosts none of the actual content of the code that needs to be run. As this is a scraper, the heavy lifting of the code is housed in the scraper file.

# The Object Being Scraped
In this case I am scraping restaurant reviews, so the purpose of this file is to house the number of objects that get created once the scraper method is called. 

# The Scraper
This is the powerhouse to the code. As the project is a scraper a bulk of the driving code is house here. This is where nokogiri and open-uri are called. Everything else had to be set up before this file could be run. The most complex part of the project lies here as, finding the parts of the CSS to scrape was the most time consuming. 

Additionally the challenge was figuring out how to separate the review and sync it to the restaurant title as it was all part of the same page.

I ended up creating another array for the reviews and matching it to the index of the restaurants.
