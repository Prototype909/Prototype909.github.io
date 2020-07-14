---
layout: post
title:      "belongs_to, has_many , has_many through macros"
date:       2020-07-14 00:45:56 +0000
permalink:  belongs_to_has_many_has_many_through_macros
---


**Belongs_to, Has_many, Has_many though**:

It didn't take long once I got into Ruby that I incounter Macros. Once I wrote my first class, it quickly becomes apparent that I am going to need to be able to manipulate instance attributes. One thing that has been drilled in my head is that as programmers we are lazy, and I am not about to write both a reader and a writer method for each attribute. Quickly i learned about the attr_accessor macro for the attributes in my class definition. I was quickly was willing to accept whatever sorcery was going on, but like most rubyist, I am learning Rails, and look!!! More Macros!! Specifically in ActiveRecord, which comporises the "Model" layer of the "Model-View-Controller" framework around which rails is designed. For example, models inherit form ActiveRecord's  base class and have access to macros such as has_many, and belongs_to, has_one, etc. which establish a relationship between your models.

So, enough sorcery, I need to figure out what is really going on here. And I don't think I will need to use my wand.

I already know that i can build our classes so they associate with one another. I also know that it takes a lot of code to do it. ActiveRecord associations allows me to associate models and their database tables without haveing to write tons of code, it makes working with our associates objects quicker, neater and easier. Lets take a topic that we I am familiar with, a fictitious music playing app. This app will catalog songs and their associated artists and genres. We will have three modles: Artist, Songs, and Genres. The relationship between artist, songs and genres is as follows:

- Artist has many songs and songs belongs to an artist.
- Artists have many genres through songs.
- Songs belong to a genre
- A genre has many songs
- A genre has many artists though songs.

We build these associations through the use of ActiveRecord migrations and macros.

The Song Model:
A song will belong to and artist and belong to a genre. Lets think about whta that table will look like. We can see that the song table will have an artist_id column and a genre_id column. This will give a song a value for the artist and genre it belongs to. Thse are considered foreign keys and n conjunction with the Active Record association macros will allow our query to get an artist's songs or genres, a song's artist or genre, and a genre's songs and artists entirely through Active Record provided methods on our classes.

The Artist Model:
An artist will have many songs and it will have many genres though songs. These associations will be taken care of thorugh macros, which I will get to in a moment. What do I mean by though songs?  The table songs is the JOIN table. This mean s that the songs table has both an artist_id and a genre_id to combine those two tables together in a many-to-many relationship.

The Genre Model:
A genre will ahve many songs and it will ahve many artists through songs. Another associations that will be taken care of through marcos, I know ill get there in a moment still.

**Building our Associatiosn using Macros**

A macro is a method that writes code for us, and by invoking a few methods that come with ActiveRecord, we can implement all of the associations I just wrote about using the has_many, has_many thoguh and belongs_to methods.

We first define our Song class to inherit from ActiveRecord::Base. This is extreamly important because if we dont inherit from ActiveRecord Base, we don't get our macro methods. We need to tell the Song class that it will produce objects that can belongs to an artist and also belongs to and genre by using the belongs_to macro.

We also need to define our Artist class to inhearit from ActiveRecord::Base amd tell the Artist class that each artist object can have many songs by using the has_many macro.

Now, because our songs table has and artist_id column and becuase our Artist class uses the has_many macro, and artist has many songs.
An artist has many genres through songs, therefore we will use the has_many though macro in our Artist call as well.

We now need to define our Genre class to inherit from ActiveRecord::base to get those macros. A genre can have many songs so we will use the has_many macro. A Genre aslo has many artists though its songs, so we will also implement this relationship with the has_many though macro.

In conclusion, the order and direction of operations does matter when establishing associations between models. and as we have just read, with just migrations and ActiveRecord macros, we can start to build and persist associations between things!
