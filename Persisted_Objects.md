Persisted Objects
==========================

Only one type of object is persisted in the Database: a Build object. As we mention in the component analysis, the Build object is best visualized in a non-relational format, so we'll use MongoDB to persist it with embedded object like `repository` and `author`.

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