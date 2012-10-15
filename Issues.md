Architecture Issues
==========================

# Solved

For the most part, we did not struggle very much with the architecture. Between the 3 of us, we have a lot of experience building similar systems (web applications), so we drew a lot from our past mistakes and successes.

That being said, the largest issue we had was wrapping our head around doing an architecture that wasn't really object oriented. In most of the examples we read about, the systems were really focused around hierarchies of objects. While we have Build objects, for the most part, our system is distributed across a variety of prebuilt components (there's no need to build a web server from scratch). Therefore, this left us in a situation where our architecture was primarily about putting together the right pieces. At first, we didn't understand if this would be OK, but after talking to Mark, everything was cleared up.

# Outstanding

We had some uncertainty around whether or not to build our workers to take tasks synchronously or asynchronously. For large projects, asynchronous work would be absolutely necessary, but for smaller projects we it mostly useless and occasionally problematic. For that reason, we decided to implement a synchronous worker instead of many asynchronous. However, we remain somewhat uncertain of this decision.