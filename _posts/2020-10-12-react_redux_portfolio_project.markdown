---
layout: post
title:      "React Redux Portfolio Project"
date:       2020-10-12 17:45:47 -0400
permalink:  react_redux_portfolio_project
---


This Project is special in the sence that it is my final portfolio project. Its hard to believe that I am finaly here at the end of this program, looking back it was quite a journey. One thing i have learn during my time and with this project is that I am not afriat to jump in and investigate, and play around with code, becuase I know that failing, trying, testing, etc. is all part of the process. And what a process this project was. I want to  mention that this project is the second attempt at the React/Redux portfolio project. My first attemp was the grandiose idea of building a recipe book. My first attempt was really flexing and showing off everything I learned and the project quickly becaome huge. There was user signup and signin, thrid party authentication, sessions, comments, likes, etc. Things with the first project was looking really good, but i ran into a few bugs at the end that i just couldn't figure out. Even some professional Dev friends of mine got stumped! So I decided to put that on the backburner and finish it up at a later date. I started over after two weeks into the project and made a really simple verson that just met project requiremets.

The project is a simple recipe book where someone can add a recipe title, a ingredient and preperation instructions as well as a image link for tha recipe. 

The back end is simple, only one table that takes in a string of title, text and image link,. I only have one recipe model that validates the title, text and image link. A simple serializer for the same attributes as well as a recie controller that housed an index, create, and show method.
 
 The front end features are a simple nav bar that links you to the home page, the recipe page, and the add a recipe page, to meet requirements of stateless components I added a simple organization function to sort the recipes by A to Z or Z to A.

Everything is nicly organized thanks to React and Redux. there I a Recipe actions that houses my fetch and post request. a components folder that holds all my stateless functions. A recipe and create recipe container for my functions that require state changes. a reducer that takes previous state and an action, and returns the next state. And of course my app.js and index.js files. 

There is some simple .css to make this simple application look nice. It was a fun project to build even if its a stipped down version of my first attempt. I look forward to finishing up the grandiose one and adding it to my portfolio. 

Thanks for everything Flatiron, its been a fun journey!

