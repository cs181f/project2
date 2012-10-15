High level description of runtime components
==============================================

# Application Server

The core of Rosie is the application server. This server will be built on the Flask framework and will expose two main interfaces: (1) a JSON API that interacts with the Github API and (2) an HTML frontend that the user can navigate. 

The server's primary responsibility is to handle the post-recieve WebHook from Github. This webhook POSTs data to our server in the following form:

'''json

{
  "before": "5aef35982fb2d34e9d9d4502f6ede1072793222d",
  "repository": {
    "url": "http://github.com/defunkt/github",
    "name": "github",
    "description": "You're lookin' at it.",
    "watchers": 5,
    "forks": 2,
    "private": 1,
    "owner": {
      "email": "chris@ozmm.org",
      "name": "defunkt"
    }
  },
  "commits": [
    {
      "id": "41a212ee83ca127e3c8cf465891ab7216a705f59",
      "url": "http://github.com/defunkt/github/commit/41a212ee83ca127e3c8cf465891ab7216a705f59",
      "author": {
        "email": "chris@ozmm.org",
        "name": "Chris Wanstrath"
      },
      "message": "okay i give in",
      "timestamp": "2008-02-15T14:57:17-08:00",
      "added": ["filepath.rb"]
    },
    {
      "id": "de8251ff97ee194a289832576287d6f8ad74e3d0",
      "url": "http://github.com/defunkt/github/commit/de8251ff97ee194a289832576287d6f8ad74e3d0",
      "author": {
        "email": "chris@ozmm.org",
        "name": "Chris Wanstrath"
      },
      "message": "update pricing a tad",
      "timestamp": "2008-02-15T14:36:34-08:00"
    }
  ],
  "after": "de8251ff97ee194a289832576287d6f8ad74e3d0",
  "ref": "refs/heads/master"
}

'''

The server must parse that JSON, split the commits into seperate builds, store them in the DB and then start a worker thread if one is not already running. All of this should be reasonably simple. 

# Build Queue

The build queue will be a simple in memory queue that the Application Server adds to on a post-recieve webhook from Github. It is accessible by the server and the worker threads. 

# Synchronous Worker Thread

The worker thread builds the user's project in the background and then posts the results to Github and stores them in the DB. The worker is started by the server when a a Github web hook hits the build API route. There are two primary functionality cases for the worker: (1) it builds the build, checks the queue, which is empty and then terminates; and (2) it builds the build, checks the queue, which has builds remaining, then builds the next one until the queue is empty.

# Database

The database is used to store the builds. It interacts with the Application Server and the Synchronous Worker Thread. When a new build is published, the Application Server takes the information from Github, creates a new Build object and persists it in the database. Then, after passing the Build.id to the Synchronous Worker Thread, the Thread retrives the Build information, builds it, and updates the Build object with the build results. When a user wants to see a build history, the Application Server loads the neccessary Build objects from the Database and displays them in HTML on the front end.

# Configuration File

The configurations for Rosie are stored in a configuration file.
