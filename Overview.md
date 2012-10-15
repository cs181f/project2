Architecture Overview
================================

There are 4 primary components of the architecture for Rosie: the Application Server, the Build Queue, the Synchronous Worker Thread and then Database.

The Application Server is the unit that ties everything together. It provides a JSON API that interacts with Github web hooks to build when new code is pushed and a HTML front end to allow the user to easliy config the server and view build history. 

The primary function provided by the entire architecture is the ability to build a build when new code is pushed to Github. The flow looks like such:

New code is pushed to Github and Github POSTs to the Application Server's build route with a set of JSON data describing the new code. The Application Server takes this JSON data, splits it into multiple commits if there are multiple commits and then stores each commit as a Build object in the database. With the Build objects persisted, the Application Server enqueues the Build.id of both objects onto the Build Queue. With the Build ids enqueued, the Application Server checks to see if Synchronous Thread Worker is running. If it is, the Application Server logic ends. If it is not, the Application Sever starts a new Synchronous Thread Worker.

When a new Synchronous Thread Worker is started, it dequeues the first Build id on the Build Queue. With that id, the Synchronous Thread Worker queries that database and loads the Build object. With the Build object on hand, the Synchronous Thread Worker executes whatever the build command is that the user specified in the configuration, which executes in Bash and returns a status code (error or success). If the build succeeds, the Synchronous Thread Worker updates the Build.status. If the build fails, it updates the Build.status and stores the stack trace in Build.error. Now, it pushes the results to Github and any connected services (like Campfire).

Next, the Synchronous Thread Worker checks if the Build Queue is empty. If it is, the worker terminates. If it is not, it dequeues the next Build.id and does the same process.

For the viewing of the build history, the Application Server loads the relevant Build objects and displays their information in HTML.
