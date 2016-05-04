# Mongo Connection String Builder

Mongo Connection String Builder is an NPM module whose sole purpose is to a mongo connection string with details like user, password and any number of conneciton options. The username and password are set using the ENV variables **MONGO_USER** & **MONGO_PASSWORD**. If these ENV variables are not set you get a valid mongo connection string back without any authentication details. 

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
var connectionString = mcsb.getAuthenticatedConnectionString("mongodb://localhost:27017/dbname", options);

//example usage of the connection string
var someMongoLib = require('someMongoLib');
someMongoLib.connect(connectionString);

```

###Setting the ENVs manually (Danger Will Robinson)
```javascript
process.env.MONGO_USER = 'user';
process.env.MONGO_PASSWORD = 'password';

var mcsb = require('mongo-connection-string-builder');
var connectionString = mcsb.getAuthenticatedConnectionString("mongodb://localhost:27017/dbname");

//example usage of the connection string
var someMongoLib = require('someMongoLib');
someMongoLib.connect(connectionString);

```




