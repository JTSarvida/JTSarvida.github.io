---
layout: post
title:      "Sinatra Project: Write to Be pt. 1"
date:       2019-01-15 08:00:52 -0500
permalink:  sinatra_project_write_to_be
---


Hello again! My basketball simulator project passed with flying colors, which was great considering how much time I had spent on it. Since then I've been hard at work to learn as much as I can and proceed smoothly with Flatiron. This time around, I am going to be creating a CRUD (Create, Read, Update, Delete) app which follows the MVC (Models, Views, Controllers) format and uses ActiveRecord with Sinatra. The project requires several things:

* Build an MVC Sinatra application.
* Use ActiveRecord with Sinatra.
* Use multiple models.
* Use at least one has_many relationship on a User model and one belongs_to relationship on another model.
* Must have user accounts - users must be able to sign up, sign in, and sign out.
* Validate uniqueness of user login attribute (username or email).
* Once logged in, a user must have the ability to create, read, update and destroy the resource that belongs_to user.
* Ensure that users can edit and delete only their own resources - not resources created by other users.
* Validate user input so bad data cannot be persisted to the database.
* BONUS: Display validation failures to user with error messages. (This is an optional feature, challenge yourself and give it a shot!)

When I came up with the idea of the basketball simulator, I decided I wanted to create something based off of my wants and interests. I love basketball, and scraping the web and displaying stats about basketball sounded like it would be a perfect thing for me. This time around, I want to focus on a wider audience. I want to think about a want/need that's more applicable to people other than me. Not only do I want my next application to reach a bigger audience, but I also want it to serve a more useful function. I decided to create an application that allows the user to create little notes of affirmation that will be sent to a database and randomly shared with other users. People can "favorite" the affirmations they get and can correspond with those who sent out the affirmations once they've ended up favoriting each other's affirmations. This idea stems from the idea that although you may be going through some difficulties, you aren't alone. I feel as though this is something that is overlooked, and perhaps creating a community based off of these random affirmations may bring some more positivity into this world.

Now that we have a general concept down, I want to plan out how the app will work, starting with when a user is asked to register. Below is a rough idea of the sign-up process, and what happens behind the scenes with each step:

1. The user starts at our beginning route, which we will use https://writetobe.com as a placeholder (because I love this name for this app).  There are several things that need to be addressed with the beginning route. First off, if a user is logged in, then we would want to redirect to the user's own profile page (in this case: https://writetobe.com/users/:user_id). If the user isn't logged in, then it would redirect to the registration page (in this case: https://writetobe.com/register).
2. The register page will accept three fields for the user to fill in: username, email address, password. Once the user registers, it will then redirect to their own profile page.
3. There are going to be three main things that will be on the user's profile page. The first thing is going to be your daily affirmation that the user receives from the database. The user then chooses whether they favor it or not. The next thing that is on the page is a list of affirmations that the user has favorited. Finally, the last main component of the page is a link that says "Create Affirmation", which leads them to the route https://writetobe.com/create-affirmation.
4. Once on this create page, there's going to be a simple text form for the user to fill, and then a button to submit the affirmation. Once submitted, it leads them to the route https://writetobe.com/users/:id/affirmations which lists off the affirmations that the user has made.
5. In the affirmations page, there will be a list of affirmations you made, with each affirmation linking to a page for each individual affirmation https://writetobe.com/users/:user_id/affirmations/:affirmation_id.  On the bottom of this page, there will be an edit and delete button that will allow the user to do both actions respectively on the affirmation.


Now, this is a good amount of things that I have listed off for me to do, most of which may be more than what is required of this project. However, I'm listing them off here so I know what I want to ultimately incorporate into the project later on in case I don't do that initially.  Okay, now that we've planned out the project, it's time to work on it! I'll follow up with a blog post focusing on the process of working on this project! Until then, cheers!



