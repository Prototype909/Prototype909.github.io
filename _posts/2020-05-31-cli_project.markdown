---
layout: post
title:      "CLI project"
date:       2020-05-31 19:36:49 -0400
permalink:  cli_project
---


After a few weeks of the chllenging curriculum that Flatiorn provides, we are at our first project that puts the knowledge of that curriculum to the test, to write a CLI program that gathers information from a API that sorts through that data allowing the user to make requests on. This was my chance to show off everything I have learned about Ruby and make the first app that is all my own.

To start, there were lessons provided and  ample videos and information to help tackle this project as well as tips on all aspects of the project which was vary helpful. They provided the information to create a skeleton app and repository on Github. In addition, They provided question to make you think, what will the app do? what is the user experience? where will the data come from? What will you need to do with that data once you have it? How will you display that data one level deep to the user?

Before I started at Flaitiron, I was a bartender and have been for many years. Due to Covid, i was furloughed from my job and had to start thinking of a different career path, which led me to Flatiron! I wanted to create something that reflected my past and who I have been for so long. I thought, why not make a app on how to make drinks! There was a wonderful API called the cocktail database that house over 500 drink recipies and over 400 ingredients!

With all this information, I started out setting my enviroment  to require neccessary gems like pry, net-http, which connects to a HTTP server and reamins open for multiple requests; and json which provides an API for parsion JSON from text as well as generating text from Ruby objects. I set up my bin/start file to accept new instances and and load them. Next was setting up my api.rb to take in the url of the api i was using, initializing new drinks, and assing attributes to it using the writer method. It was then a matter of setting up my Drink.rb file. This file willl be responsible for keeping track of drinks attributes and save all drinks created. Finally, the hard part, developing my cli.rb which is repsonsibe for interactin with the user, and controls the flow of the program. This was challanging to say the least, setting up menus the direct the user, asks for their input and and accepts that input to then display the list of drinks.

This project put to test everything that has been taught to me over the past few weeks. It was not easy, but in the end it solidified everthing I have learned, and left me with something to be proud of.
