# Consistent Vocabulary

This was definitely one of the most glaring problems with our architecture. Luckily, it was also one of the easiest things to resolve. We updated all of our langauge to be consistent--both the diagram and the text. With the updated documents, our vocabulary is consistent.

# Document Overview 

* Putting “both objects” into the database seems to be a typo from a previous incarnation of the architecture, as it is not consistent with the rest of the description.

Fixed the typo.

# Component Analysis

* Add analysis of the components – we are confident you can use them, based on your experience, but would be clearer if there was a reason stated why these specific choices were the best ones for the situation. In fact, the MongoDB is analyzed in the “Persisted Objects” document; could move that to this document.

Gave rationale for why we decided to use each component rather than just a rationale for why we felt comfortable using it. A good upgrade from the previous analysis.

# Interfaces

* “Primary” uses were listed, but were there other uses that might be important to the architecture that were left out? Not sure if you are covering all the important interfaces by only talking about the primary ones.

Took out "primary" language and clarified what functions would be available from which interfaces.

* Contradiction with the diagram – in diagram, can build from both the HTML and the CLI; in
interfaces, can’t build from the HTML. Could use clarification about which is correct.

Aligned documents with diagram.

* CLI takes only one command to get started – didn’t understand what this meant. A few
more sentences about what this means would go a long way in making the CLI as a whole easier to understand.

Clarified that while single line installation was a feature, it was not the only command available on the CLI. Gave a list of available commands.

* Does the queue hold build objects or just build numbers? (From the meeting: just build
numbers.) Clarify this so that the reason the interface is simple is clear, not just lacking description.

Clarified across documents that Queue holds only build IDs and the queries the DB for the actual object.

* Web front end is shown as having only a single part, but it seems there are actually
multiple different parts included. Should go into more detail about the interface with the user, etc.

Clarified multiple user scenarios for the web front end

* In the solved issues, clarify what you talked to Mark about and why that helped you solve them. We didn’t understand that the solution was that it didn’t matter that it wasn’t object-oriented, so we thought the issue was still at large, though approved by Mark.

Gave clearer explanation for why we realized this issue was not serious, took out ambiguous language about talking to Mark.

* In the outstanding issues, put more justification of why synchronous was chosen – you
actually said it to us during the meeting, so add it to the document! “Worker thread – only one, so synchronous, but asynchronous to the application server” was the comment if I wrote it correctly. There was justification and clarification when we were talking to you, so that would clear up the uncertainty in the document.

Update language across the entire document to make more clear the distinction between synchronous and asynchronous worker thread. Updated the outstanding issue to clarify that if in the future we realize that Rosie should be usable with large scale applications, then there will need to be serious architectural changes to manage multiple asynchronous workers.

# Persisted Objects

* In MongoDB, move the explanation to the component analysis. For more info, look at the issue raised in the Component Analysis section.

Made appropriate movements of content.

# Rosie Architecture

* How do the build results get put into the database? Nowhere in the documentation is it clear that they are actually put there, but it is clear that they need to get there somehow for access later.

Updated document language to clarify that the Worker Thread updates the Build object in the database with the Build results after it is done building.

# Runtime Components

* Clarification of why the “code” is included. In meeting, explained very clearly that it dictates how the API must respond, so that should go in the paragraph before the code to make it clear why it’s there.

Clarified that this was the format of the JSON data that the Github API will pass our application. In the run time component section to give an idea of what form the information our Application Server will need to handle will be in.

* Clarification/description of what the configuration file actually is and where it should be
stored. (During meeting: standalone file that will be figured out during implementation.) Should add this to the description.

Updated write up of configuration file to clarify when it will be created, updated, and read from.

