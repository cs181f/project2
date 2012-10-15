Component Analysis
============================

The largest chunk of our Component Analysis came from past projects that we have completed using the technologies we are planning to use. Here, I'll go through the technologies and list where our analysis occured.

# Flask

Both Brennen and Jesse have a lot of experience using Flask as a web framework. For the project they are currently working on, they have written over 2000 lines of Flask code.

# MongoDB

Jesse has used MongoDB for a variety of projects, writing over 500+ lines of model/object code using MongoDB ORMs (MongoMapper and Mongoid). While the majority of that code was written in Ruby, his experience with the database has shown that it is extremely well suited to the structure of the Build object.

Additional support for the architecture came from examining another open source CI server: CIJoe (https://github.com/defunkt/cijoe). We borrow the in memory queue idea from them.

All in all, we are confident that our current architecture is well suited to solving the problem at hand.