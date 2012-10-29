Architecture Issues
==========================

# Solved

For the most part, we did not struggle very much with the architecture. Between the 3 of us, we have a lot of experience building similar systems (web applications), so we drew a lot from our past mistakes and successes.

That being said, the largest issue we had was wrapping our head around doing an architecture that wasn't really object oriented. In most of the examples we read about, the systems were really focused around hierarchies of objects. While we have Build objects, for the most part, our system is distributed across a variety of prebuilt components (there's no need to build a web server from scratch). Therefore, this left us in a situation where our architecture was primarily about putting together the right pieces. After further consideration, we decided that this was not an issue because most web applications are not built in a OO manner.

# Outstanding

One of the feature sacrifices we made when defining our requirements was that Rosie would not be built to work with large projects. For this architecture, this means that rather than having multiple Worker Threads that build builds both asynchronously to the Application Server and asynchronously to each other, we will have a *single* Worker Thread that will build builds in order, but asynchronously to the Application Server. We have decided this is an outstanding issue because in the future we may need to readjust our architecture if we deem scalability for large applications a necessary feature.