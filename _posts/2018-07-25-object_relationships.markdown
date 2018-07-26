---
layout: post
title:      "Object Relationships"
date:       2018-07-26 00:13:57 +0000
permalink:  object_relationships
---


There are multiple object relationships to keep track of:

**Belongs To**
Prime Example: A song belongs to an artist

How to set up:
1. The owner object needs to be listed as an attribute reader
2. The owner object needs a custom writer that reciprocates by doing the following:
  a. set the argument to the instance variable
	b. push the instance into the has_many array if not already included

Example:

class Song
attr_accessor :title, ***:artist***

def initialize(title)
  @title = title
end

def artist=(artist)
 @artist = artist
 artist.songs << self
 end

end

**Has Many:**
Prime Example: An artist has many songs

How to set up:
1. The object being referenced needs to be set to an empty array
2. Objects are added into the array upon function call.
3. The class needs to be able to read the object being referenced

Example:
class Artist
attr_accessor :name
attr_reader :songs

def initialize(name)
@name = name
**@songs = []**
end

def add_song(song)
@songs << song
end
end

**Has Many Through**
Prime Example: 
1. An Artist has many songs
2. The song belongs to a genre
3. An artist has many genres through their songs
4. If the artist can access the song it also has access to the genre and its attributes

Examples:
1. An owner has many pets
2. The pets belonged to a shelter, and when adopted belong to an owner: they can belong to an owner or a shelter
3. The shelter has many pets
4. The owner has many pets
5. The owner has relationships with the shelters through the pets

How to set up a dog belonging to a shelter?
1. Shelter has to be listed as an attribute for the dog.
2.  Created a reciprocated has_many function

How to set up the has_many_through relationship 
1. Create a custom reader for the owner
2. Run a collect method on the object that connects the owner and the has_many_through object

class Shelter   #have many dogs 
  attr_accessor :name, :city
  attr_reader :dogs

  def initialize (name, city)
    @name = name
    @city = city
    @dogs = []
  end 
  
  def add_dog(dog)
    @dogs << dog #adds to shelter.dogs
    dog.shelter = self if dog.shelter != self 
  end
  
**  def owners
    @dogs.collect{|dog| dog.owner}.uniq  
  end**
  
end 





