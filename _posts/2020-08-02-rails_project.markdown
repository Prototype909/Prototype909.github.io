---
layout: post
title:      "Rails Project"
date:       2020-08-03 01:33:11 +0000
permalink:  rails_project
---

For my rails project, I build off and expanded on the same idea that i used for my Sinatra project, a film database where a user can add details regarding a fim, i.e. name, director, year, genre and a discription. Once the film is created, a user can leave comments about the film. This project was but on rails, a web framework thta provides developers the tools they need in order to build a application. While every application i unique there are certain components taht can be found and is the core of almost every applicaton, such as: routing, asset management, database connections, etc. A good web frameworkd gives developers these baseline tools so that dont have to create the base application functionality for each new project.

Rails is a MVC, Model-View-Conroller, framework. This essentially means that Rails takes advantage of the application architecture that helps developers naturally separate concerns and organize their applicaton properly. This setup encourages a specific set of conventions, such as placing the logic for the application in the model files, managing the code flow in the controllers, and displaying content to the user in the views.

The process of building this app was very fun and equally challenging. 
Some of the factors that i needed to take into consideration from the beginning were:

* creating a database tables that took in user attributes such as username, email, and a password_digest. A films db that took in a title, direction, year and description. A comments db that took in a text body. And a genre table that took in a name. 
* Creating modles for the matching db just mentioned. Models are a critical aspect of the application as this is where you have direct access to the specific database that include complex db queries, data relationship, and custom algorithms.
* Setting up necessary CRUD and RESTful routes.
* Settign up nested routes
* Implementing Google Oauth
* Maintainseparation of concers with helper methods and partials.

In the beginning a very important part of the project was setting up the relationships between different models. This part has always been tricky, although I like to think I am getting better at it. Setting up the has_many and belongs_to is crutial. A user has many films, and has many received_comment through films. a user also has many comments and many commented_films through comments. Further, a film belongs_to a user as well as a genre, and has_many comments and has many users though comments. A comments belongs to a user and a film. As well as a genre has many films. Geez, putting it all in place is like a toungue twister as well as twisting the mind puting it all together! In this project the join table was film, taking in a foreign key for user and gene, which gave me a many-to-many relationship that i needed.

One of the new features of this application that was really cool to learn was implementiong Google Oauth. It wasa little challanging but fortuantly my cohort lead created a excellent walkthough blog that made it a really easy step-by-step process. Something that i took for granted with apps i use every day, I know know what is happening and how it is set up and working in the background. So cool to know that my app sends a authorization request to google. Google then authenticates the user's credentials within their own system, then sends a callback function back to my application with the users credentials. Finally, my application creates a new user in my db using those credentials, specificallly the UID and email. 

Overall, I am very happy with the program, my developing of understanding what is happening and why. If I had to think of areas of inprovement I would have to say that I would like to get better at DRYing up my project, and as always refactoring to make it cleaner.



