# Jesse's Notes

Here are my thoughts on the architecture:

iPhone UI prototype and interface discussion:

This looks really good, had no concerns here.

SQL component analysis:

I understand that you all are just getting to know SQL, but I'd like to see a little more detail here. The problem is, while you've decided on using SQL as your database, you haven't outline *how* you'll be storing and accessing your data. Specifically, here are some questions: 

Where is the discussion of the different objects (Plant, etc)? 
Where is the discussion of what attributes those objects will have?
What components of your application will access the database and how will they do this (will you use an ORM)?
General Architecture Overview:

OK, I like what you do going over the different sections of your application in detail, but to be honest I don't think that these are the components you should be overviewing. Yes, these are different things that either your user will interact with (i.e. the homepage) or a developer will need to supply (i.e. database), but I my understanding of what the components of an architecture are is a little different.
Instead, I think you should be overviewing what technologies you will need to compile to make this all work and how they will all work together. My primary concern is that you haven't discussed a central application server. I assume that this will be necessary (unless you plan to not keep track of users at all and never update your database of plants). Some specific questions:

Are you going to have an application web server that stores user and plant information? If so, how is the iPhone going to communicate with that? 
Are you going to have separate databases on both the iPhone and the server? 

In general, I think that you all do a good job of describing your application, but I don't really see an architecture for how it's going to be built. I know that is pretty harsh, and I know that you all are just getting to know most of these concepts, but as I said earlier, I try to give as honest feedback as possible.

In exchange for being so critical, I'd like to make an offer: if you're interested, I'd be happy to sit down and talk you all through the basic interactions between a web server and an iPhone app, how a web server is put together, what an ORM is, etc etc. Most of this stuff is never even glossed through in school, and I know from experience that it can be pretty overwhelming when you're first getting into it, so I'm happy to help in any way I can. Let me know if that might be something you're interested in! 

# Linnea's Notes

The biggest issue, and one I wanted to bring up before going into a point-by-point discussion, is that the architecture is very unclear about this "wiki" that is repeatedly mentioned in the overview. Is there both a wiki and a separate, secondary database? Or is the SQLite database that is heavily discussed the database underlying the wiki? I felt this was very confusing.

If there is going to be some sort of wiki, what wiki software will be underlying it? Where will it be hosted? Who is allowed to edit it - s that part of the application? Your detailed component analysis only discussed the SQLite database, and said nothing about a wiki; I believe a lot more details are needed here.

And just as a quick heads up, did you choose SQLite because it is provided by the iOS SDK (out of box)? Did you research what other useful resources might be provided by the iOS SDK?


Now just going through the overview in order, some other major points:

* Regarding your data:
  * Where is your data going to come from?
  * How easy will it be to maintain and add to the plant database? The search function?
  * If users submit error reports (how?), will they be updated in a timely manner?
* You mention two search functions search.
  * What does "a list of keywords to plug into the keyword of the database" mean?
  * Are you planning to implement the search algorithm yourselves?
  * If not, what resources will you consider to handle the search?
  * You mentioned in "outstanding issues" that you were aware that the search function would need more research as to how the users would use it so I'll leave that part be for now, but I recommend getting that research done sooner than later. You may need to know what categories you need quite early on.
* As discussed above:
  * I would love to see more clarity on how/if the locally stored database will communicate with any central information stores, and if there is *also* a wiki, how all of these will interact.
  * Is the application just formatting information from the database and displaying it, or is the database only used to provide a particular wiki page with more information?
  * **A diagram would go a long way here.**
* If you are going to have a central server with the information on it:
  * Where/how are you hosting it?
  * Do you know if/when you will need to scale?
  * If your users will be keeping local copies on their devices:
    * How often will the databases sync?
    * Have you considered how much traffic to/from the central server you will need to accommodate?
    * Have you done any predictions on how big this database will be on the user's devices?
* Finally, for the UI:
  * On the last slide, "Identification" and "My Plants" switched suddenly.
  * I noticed that there was no discussion of potential preferences, even as simple as "There will be none". Some potential preferences may be best built in from the start.
  * And lastly, have you considered how the application will scale between an iPhone and an iPad's larger screen?

  # Brennen's Notes

  I want to raise a few issues with your architecture.

First, I think that your architecture is lightest around the database structures, where there should be more complexity. As you note, this is an area that is new for your team, but that's precisely why you should have taken the time to flesh out the pieces / structure of your database.

Second, your architecture seems to imply that the app is entirely structured around the UI and should do more to explain what non-visible components of the app are in action. It is also unclear if there is a backend server, as you had previously discussed, powering the app, or if the data is contained within the app as I had suggested.

Third, though you described the components of your interfaces, there is not very much detail about the information being passed among them, which could lead to confusion in implementing those interfaces.