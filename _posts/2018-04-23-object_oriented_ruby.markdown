---
layout: post
title:      "Object Oriented Ruby"
date:       2018-04-23 20:46:45 -0400
permalink:  object_oriented_ruby
---


There's actually a lot here. 

So I started my journey with Javascript with Fullstack Academy's Bootcamp prep. I started feeling quite familiar with JS by the end of that program carried a lot of that over to my learning for Ruby. I've been breezing along the program for awhile now however...

There were a few things about Object Oriented Ruby that halted that progress. In other words there were a few things I hadn't done yet in JS which is classes and instantiation.

So here are a few things that were new with Object Oriented Ruby:

1. Classes and Instances and (Instance Variables)
 
 I never got into classes with Javascript. So what's interesting is learning about how to reuse code in the form of classes. There's a few new things to learn here.
 
 1. A Class is a blueprint and a factory: it can bring to life new kinds of objects and it can define what those objects do

**Class Definition and Class Body **
 The format looks like this:
 
 class Dog <-- This is a class definition
 !---This would be the class body --!
 end <--this ends the class
 
 **Instantiation**
 Instantiating is what it sounds like. It means creating a new instance of an object predefined in a class. It is done by doing the following:
 
fido = Dog.new

# Sidebar
when you use " " ruby translates it to string.new

# Resume
**Initialization**
Next, after you create a class you want to initialize the class with the following format:

class Baby
  def initialize #callback
	  cry
	end
	  
		def cry #instance method
		  puts "Waaaa"
	end
end

The initialize method is a callback/hook/life cycle event because it is a method that gets automatically fired by another method.

The instance method are methods that can be called in each instance of the class.

**Writer and Reader**

> class Baby
>   def initialize #callback
> 	  cry
> 	end
> 	  
> 		def cry #instance method
> 		  puts "Waaaa"
> 	end
> 	
> 	def name = (the_baby_name) #writer
> 	  @my_name = the_baby_name #casting the local variable to an instance variable
> 		end
> 		
> 	def name # Reader
> 	  @my_name
> 		end
> 	end
> 		
> end

**Instance Variables**
In a class, to create a method you need a writer and reader for methods. The writer allows you to create new instances of the method. The reader allows ruby to read the output of the method. The issue when creating writer and reader methods is that you have a problem with scope. Creating regular varibles are locked in the scope of the local function. Global variables are not an option as they cannot be unique to each individual instance; this is called internal state. For that reason you have to use an instance variable @variable. Instance variables are localized to the scope of the instance.

Casting is setting data and hoisting it to the scope of the instance variable.

**Accessors, Writers, and Readers**
For the sake of succinctness we do not have to write a new writer and reader method for every attribute we can simply do the following:

> class Baby
>   attr_accessor :name, :weight, :eye_color, :birthplace, :birthdate #this creates both writer and reader methods
>   attr_writer :location #this creates a method location equals location =() and creates a writer method
>   attr_reader :dna #this creates a reader for dna

**Class Variable and Self**
An instance variable is responsible for holding information regarding an instance of a class and is accessible only to that instance of the class. A class variable is accessible to the entire class––it has class scope. A class method is a method that is called on the class itself, not on the instances of that class. Class variables store information regarding the class as a whole and class methods enact behaviors that belong to the whole class, not just to individual instances of that class.

Self is representative of the object receiving the method call.


