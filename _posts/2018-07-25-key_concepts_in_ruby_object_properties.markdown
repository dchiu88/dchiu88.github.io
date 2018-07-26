---
layout: post
title:      "Key Concepts in Ruby Object Properties"
date:       2018-07-26 00:14:12 +0000
permalink:  key_concepts_in_ruby_object_properties
---


Setter Methods:

Setter methods are writer methods. A setter method is defined with an =, equals sign, appended to the name of the method. The = is followed by the (argument_name). They look like this:

def name=(name)
  @name = name
end

To call a setter method, you use the . notation (dot notation) to call the method and set it equal to a new value.

kanye = Person.new("Kanye")
 
kanye.name
  => "Kanye"
 
kanye.name = "Yeezy"
kanye.name
  => "Yeezy"

Getter methods are reader methods. They areturn information stored in instance variables. They look like this:

def name
  @name
end

Setter and Getter methods are used to read and write to the respective properties in the objects. These are used to set and get values for instance methods.

Setters and Getters are also required in order for Objects to Collaborate. In order for one class to be able to read the properties of another class it will need an attribute reader titled after the name of that class.

To reciprocate a relationship the attribute reader needs to be redefined as follows:

class Dog
attr_accessor :name, :breed, :owner

def owner=(Owner)
  @owner = owner
	owner.pets << self
end

end

class Owner
  attr_accessor :name, :pets
	
	def initialize
	  @pets = []
		end

end
