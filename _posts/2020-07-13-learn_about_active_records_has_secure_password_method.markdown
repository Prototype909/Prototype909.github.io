---
layout: post
title:      "Learn about Active Record's has_secure_password method."
date:       2020-07-14 02:25:28 +0000
permalink:  learn_about_active_records_has_secure_password_method
---


It seems common sense to secure a users' data. Like most people, despite warngins against it, most users will use the same username and password combination across many different websites. Because of this, we never want to store our users name and password in plain text in a database. Instead we run the password though a hashing algorithm.  hashing algorithm manipulates data in such a way that it cannot be un-manipulated. This is to say that if someone got a hold of the hashed version of a password, they would have no way to turn it back into the original. In addition to hashing the password, we'll also add a "salt". A salt is simply a random string of characters that gets added into the hash. That way, if two of our users use the password "12345", they will end up with different hashes in the database.

We use an open-source gem called 'bcrypt' to implement this. Bcrypt will store a salted, hashed version of our passwords in the database in a column called 'password_digest. Basically once a password is salted and hashed, there is no way for anymore to decode it.

Before we get into ActiveRecords has_secure_password macro, let's talk a little more about about implementing BCrypt. When you create a ActiveMethod migration you will need to create a column for password_digest, as a string, along with any other column you might need to create. run your migrate with rake db:migrate. Its good practice to double check  your schema to make sure that everything migrated successfully.

Once you created your migration that included password_digest and checked that it migrated successfully in the databases schema, lets update our model so that it includes 'has_secure_password'. This ActiveRecord macro gives us access to a few new methods. Remeber, a macro is a method that when called, creates methods for you, just like calling a normal Ruby method. The has_secure_password macro works in conjunction with the gem BCrypt that was mentioned earlier in this blog, and give us all those abilities in a secure way that doesn't acutually store the plain text password in the database. Has_secure_password, adds methods to set and authenticate against a BCrypt password.

For example, we created a User class that inherites from ActiveRecord base. that has_secure_password written.

class User < ActiveRecord::Base
  has_secure_password
end

Next, when creating a Post '/signup' action we would need to make a new instance method of our user class with a username and password from params.

For example:

post "/signup" do
  user = User.new(:username => params[:username], :password => params[:password])
end

It is important to mention that even though our database has a column called password_digest, we still access the attribure password that is given to us by has_secure_password. Becuase our user has 'has_secure_password', we wont be able to save this to the database unless our user filled out the password field. If we called user.save, this would return false if theuser can't be persisted. 

If we created a valid user by writing a login method like this:

post "/login" do
  user = User.find_by(:username => params[:username])
end

This would create a vaild user that we would need to check two conditions on. Did we find a user with that name and we need to check if that user's password matches up with the value in password_digest. A user must have both an accout and know the password.

W validate password matchs by using a method called 'authenticate' on our Users model. Its importat to note that we don't have to write this method ourselves, its added when we added the has_secure_password line of code to our Users model! We told Ruby to add an authenticate method to our class when the program runs behind scenes!

To Recap a little, lets walk though the process of how a User authenticate method works. 

- it takes a string as an argument
- it turns the string into a salted, hashed version
- it compares this salted, hashed version with the user's stored salted, hashed password in the database
- if the two versions match, authenticate will return the User instance, if not, it returns false.

In this code example that will follow, we can see how we can ensure that we have a User and that User is authenticated. 

post "/login" do
  user = User.find_by(:username => params[:username])
 
  if user && user.authenticate(params[:password])
    session[:user_id] = user.id
    redirect "/success"
  else
    redirect "/failure"
  end
end

If the user authenticates, we will set the session[:user_id] and redirect to the /success route. Otherwise, we will redirect to the /failure rout so the user can try again. 

This is the basic authentication system for a user without storing a plain-text password in our database, provided by our BCrypt gem in conjunction with the macro has_secure_password and validated invisibly by Ruby's authenticate method.


