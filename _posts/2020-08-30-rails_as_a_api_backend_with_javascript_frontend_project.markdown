---
layout: post
title:      "Rails as a APi backend, with JavaScript frontend project"
date:       2020-08-30 23:28:28 +0000
permalink:  rails_as_a_api_backend_with_javascript_frontend_project
---


For my JavaScript project i wanted to diversify my portfolio a do somehting not movie related, which is what my Rails and Sinatra project were based on. I decided to create a app for my partner who loved to cook. This app would become a recipe book that would take all his favorite recipes he finds on the internet and keep them in one place; this should score me some bonus points with him!!

The application has a form where you can type in the title of the recipe you want to add, a link to the image of the recipe, a link to the recipe and a text area where you can enter the ingredients. The ingredient text just creates a bullited list of what goes in there, not the acutal measurements. once the recipe is created you get a nice little card that shows the image, name, ingredient list and a link to the recipe.

This was probably the hardest project that I have done to date. I have struggled hard with JavaScript but was able to produce a working application. The backend creation was the easiest as its all ruby and was things I have done before, like creating the DB, which took in three tables. The first was recipes that took in a title, recipe link and image link. Second was ingredients, which took in a name. The thrid table was the join table and referenced both ingredient and recipe ans foreign keys. I also seede some data that created a recipe with those attributes as well as ingredients that shovled in items using .find_or_create_by, which takes the first record with the given attributes, or creates a record with the attributes if one is not found.
 
 Next was creating custom routes, and being that this is a single page application. I needed a route to get my recipes index and a post to my recipes create. I also wanted to add a feature that would take a random ingredient and show a random recipe that used that ingredient so i would need a get for ingredients index as well as a get for recipes/ingredients for a recipe show.
 
 My models have a many-to-many relationship, that has_many ingredients_reciepes, my join table, and has_many ingredients through ingredients_recipes. Ingredients has_many ingredients_recipes and has_many recipes, thought ingredients_recipes. lastly my join table, ingredients_recipes, belongs_to ingredient and belongs_to recipes. Relationship are always fun to figure out, right!!! lol
 
 lastly for the backend was writing the controllers. I needed to, for ingredients and recipes. The ingredient controller was the shortest as I only needed a index that took in all ingreients and rendered json. The recipe controller neede to be buildt out a lot more as it needed a index, show and create. The project requirements needed two CRUD actions to pass. If i decided to play around with this app further i will probably add a delete option as well. 
 
And that is it for the back end!! Now the really hard part, JavaScript for the front end!!

Starting the frontend was very difficult for me. I knew I needed to add a index.html, and a index.js as well as creating a style folder that would house my CSS. 

I wanted to be able to see something so I have something to look at while I worked. I started in the index.html. I created a div with a class "container" that housed my main title, as well as my form buttons for adding a recipe and get a random recipe by ingredient. This was my first time working with hidden classes that held the new recipe form. I worked well and added a nice visual appeal to the project once done. 

I used one of our labs, the toy tale challage as a lauch point to create recipe cards that would house all the elements of the card, name, image_link, recipe_link. This was the easier part as i had some reference materail to work with. 

I knew that i needed some functions to create recipes and to add recipes to the DOM. Okay things are getting harder now as i need to create a recipe array and an ingredient array to pus all the new attributes into. 

now for event listners that would listen for clicks that would toggle forms and button and dropdown of the ingredients etc. 

I wish i was better at explaining this section, I had no problem letting you know what was happening in the backend. Doing and explaining code in this area is not easy as im still learing how things are working and why things are working. 

I can let you know that I never before have used debugging tools and the inspect section where i was reading the elemets tab, working in console as well as the sources section. Thankfully the console section provides so much information regarding errors. It was my best resouce for understanding failure after failure. 

currently all the code is housed in index.js. I am desiring to organize everything into classes and this part is way more difficult that i anticipated. i started to create files that i could move the api connetions into. A file for recipe that i could move the functionality of the app into, etc. I haven't bee successful yet as I need to go  over the main index.js and find where i use certain code and call on the new classes. Wish me luck on that. 

 


