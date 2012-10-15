Interfaces
=========================

# External Interfaces

There are 3 external interfaces: the JSON API and HTML frontend that the Application Server exposes and the CLI for setup.

## JSON API

This API allows Github to use its web hooks to queue a new build when new code is pushed. It exposes two routes '/build' and '/info'. '/build' is the POST route that Github hits with the JSON data, which then starts the build process. '/info' is a GET route that exposes informatin about the systems current status: whether it is building right now, what the last build was, and what the last build status was, for example.

## HTML frontend

There are two primary uses for this. First, it allows users to see the build history and see what causes individual builds to fail (and who wrote the code that made them fail). Second, it exposes configuration options for the server.

## CLI

This interface is primarily used in the setup stage. Ideally, it will consist of one command `rosie install,` which is run inside a clone version of the Github repo, which the user wants CI for.

# Internal Interfaces

## MongoDB ORM

To communicate with MongoDB, we will use a ORM called PyMongo. This will easily allow us to create, update, and retrieve Build objects, without dealing with messy SQL queries. This is how the Application Server and Synchronous Worker Thread will communicate with the DB.

## Build Queue

The Build Queue can be thought of as a sort of interface because it facilitates communication between the Application Server and Synchronous Worker Thread. That being said, the Synchronous Worker Thread will be spun up from inside the Application Server, so this isn't the only way they communicate.

