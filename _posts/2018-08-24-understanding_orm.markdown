---
layout: post
title:      "Understanding ORM"
date:       2018-08-24 13:24:12 +0000
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

Instead, we follow the convention: classes are mapped to or equated with tables and instances of a class are equated to table rows.

If we have a Cat class, we have a cats table. Cat instances get stored as rows in the cats table.
