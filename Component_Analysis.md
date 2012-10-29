Component Analysis
============================

The largest chunk of our Component Analysis came from past projects that we have completed using the technologies we are planning to use. Here, I'll go through the technologies and list where our analysis occured.

# Flask

We have compared Flask to other frameworks like Ruby Sinatra and Node Express.js. On the whole, these frameworks are very similar, so using one over another is a matter of preference and comfort. Both Brennen and Jesse have a lot of experience using Flask as a web framework, so that's what we are going with. For the project they are currently working on, they have written over 2000 lines of Flask code.

# MongoDB

We will use MongoDB as our database because it allows easy storage of non-relational object types and embedded objects, which is logical for the JSON format of build objects that get passed from Github. Jesse has used MongoDB for a variety of projects, writing over 500+ lines of model/object code using MongoDB ORMs (MongoMapper and Mongoid). While the majority of that code was written in Ruby, his experience with the database has shown that it is extremely well suited to the structure of the Build object.

# JSON API

Github's API is entirely JSON, so that mandates our use of JSON as the format of our data/API. Jesse and Brennen have written 1000+ lines of JSON API code using Flask, so we feel extremely comfortable implementing this component.

Additional support for the architecture came from examining another open source CI server: CIJoe (https://github.com/defunkt/cijoe). We borrow the in memory queue idea from them.

All in all, we are confident that our current architecture is well suited to solving the problem at hand.