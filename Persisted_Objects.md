Persisted Objects
==========================

Only one type of object is persisted in the Database: a Build object. 

We will use MongoDB as our database because it allows easy storage of non-relational object types and embedded objects.

# Build

A build object has the following attributes:

* repository - Object
	* url - String
	* name - String
	* description -String

* id - String
* url - String
* author - Object
	* email - String
	* name - String
* message - String
* timestamp - Date
* ref - String
* status - Integer (1 - succeeded, 0 - failed, 2 - processing)
* error - Text