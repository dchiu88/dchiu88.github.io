---
layout: post
title:      "Understanding ORM"
date:       2018-08-24 09:24:13 -0400
permalink:  understanding_orm
---


ORM is basically an integration between Ruby methods and SQL. Rather than running multiple lines of 

database_connection.execute():

database_connection.execute("INSERT INTO cats (name, breed, age) VALUES ('Maru', 'scottish fold', 3)")
 
database_connection.execute("INSERT INTO cats (name, breed, age) VALUES ('Hana', 'tortoiseshell', 1)")

We can nest these in Ruby Methods:

 def self.save(name, breed, age, database_connection)
    database_connection.execute("INSERT INTO cats (name, breed, age) VALUES (?, ?, ?)",name, breed, age)
    end
end

Now to create and save Cats what has to be done is:

database_connection = SQLite3::Database.new('db/pets.db')
 
Cat.new("Maru", "scottish fold", 3)
Cat.new("Hana", "tortoiseshell", 1)
 
Cat.all.each do |cat|
  Cat.save(cat.name, cat.breed, cat.age, database_connection)
end

In ORM there is a convention: classes are mapped to or equated with tables and instances of a class are equated to table rows.

More specifically, it is the attributes of the new instances that are mapped to table rows. We are not saving ruby objects, only the individual objects. Ergo, we are not inserting self into the database, we are inserting self.name or another attribute into the database.


