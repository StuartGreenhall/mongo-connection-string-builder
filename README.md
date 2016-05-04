# Mongo Connection String Builder

Mongo Connection String Builder is an NPM module whose sole purpose is to a mongo connection string with details like user, password and anynumber of conneciton options. The username and password are set using the ENV variables MONGO_USER & MONGO_PASSWORD. 

# Usage

###Simple use case
```javascript
var mcsb = require('mongo-connection-string-builder');
var connectionString = mcsb.getAuthenticatedConnectionString("mongodb://localhost:27017/dbname");

//example usage of the connection string
var someMongoLib = require('someMongoLib');
someMongoLib.connect(connectionString);

```
###With connection options
```javascript
var mcsb = require('mongo-connection-string-builder');

//Options with be appended into the connection string as &key=value
var options = {
  authmechanism : 'MONGOCR',
  authSource : 'admin'
}
var connectionString = mcsb.getAuthenticatedConnectionString("mongodb://localhost:27017/dbname");

//example usage of the connection string
var someMongoLib = require('someMongoLib');
someMongoLib.connect(connectionString);

```


