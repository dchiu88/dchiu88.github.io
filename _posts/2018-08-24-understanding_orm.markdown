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

Additionally, when getting data back from the database. The database returns that data as an array of rows. It is up to use to write the code to convert that back to a Ruby object.

The first thing to know is that the database, SQLite in our case, will return an array of data for each row. For example, a row for Michael Jackson's "Thriller" (356 seconds long) that has a db id of 1 would look like this: [1, "Thriller", 356].

def self.new_from_db(row)
  new_song = self.new  # self.new is the same as running Song.new
  new_song.id = row[0]
  new_song.name =  row[1]
  new_song.length = row[2]
  new_song  # return the newly created instance
end

Thus when we get the returned values from the database, we just have to iterate over each row and call the self.new_from_db method we previously created.

class Song
  def self.all
    sql = <<-SQL
      SELECT *
      FROM songs
    SQL
 
    DB[:conn].execute(sql).map do |row|
      self.new_from_db(row)
    end
  end
end


