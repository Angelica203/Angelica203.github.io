---
layout: post
title:      "Sinatra what?"
date:       2020-12-09 23:30:45 -0500
permalink:  sinatra_what
---

   
		
From building to debugging can be a headache. But the beauty of building a Sinatra application we have ActiveRecord that provides us with built in methods. Although ActiveRecord is  not the core to building a Sinatra application, it already did a big part.

 In order to make the application function properly, we still need the rest of our framework, such as all the required gems and all the folders to make it an application. 
 
 One thing that I struggled to understand at first will be in the MVC(models, views, controller) files. In our Sinatra framework contains an app folder and in that app folder is  where the MVC files are located, which are used to organize different components of the application. Inside the controller we have different requests that allow our application to respond when a user types in a url such as (www.example.com/users/signin). A get '/users' request is submitted which is processed through the controller.
 
The moment when i got confused! Within  the get pathway in our controllers we have two options to choose from when determining what to show the user, render or redirect. 

**Render**

Rendering is a view done when  calling an erb file in a path within a controller. Erb(Embedded RuBy)is an extension  in our view files under app. Rendering a file will display that view without submitting additional requests to the server. Also rendering allows us to access instance variables through the erb file.

*get  '/signin' do

*erb*  : '*users/signin*'

*end*
*
**Redirect**

Redirect is different from rendering. It sends a new get request to the server. Because of this we can't access instance variables through redirect, as those variables no longer exist once a new request has been made because of the statelessness of the server. We can use redirect when we send a request to get new  information from the user, or if we need to utilize the logic present in another path's get request.

  post '/signin' do
	****
   **     user = User.findbyusername(params[:user][:username])
				*
      *   if user && user.authenticate(params[:user][:password])*
				 
  *session[:userid] *= user.id
	
   *redirect to "/users/#{user.i*d}"
	 
    *else
		
 f*lash[:message] = "Invalid Credentials. Please try 
 again."
 *
  * redirect to '/signin'
	 *
   *end
		 
    end 

*



*
