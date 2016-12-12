# dweetio connector

About dweetio

dweet.io is a very simple set of HTTP HAPI that allow any device that can send HTTP requests to publish/subscribe message to other devices.

Purpose of the scriptr.io connector for dweet.io

The purpose of this connector is to wrap dweet.io's interfaces and expose them as JavaScript objects to your scriptr.io scripts.

# Components

dweetio/dweet: this is the main object to interact with. It provides the postDweet and getLatestDweet methods to publish a message, respectively read most recent messages published by a given device
dweetio/config: configuration file, should notcurrently be modified
dweetio/client: generic http client that handles the communication between scriptr.io and dweet.io's APIs
dweetio/stub: simple stub, used for testing in case you exceeded the number of free dweets
dweetio/test/tests: small examples on how to use the connectors' objects and corresponding methods.

# How to use

Using the connector is pretty easy. First step is to require the the dweetio module into the script where you plan to use it, then create an instance of the Dweet class passing the name of the device you're targeting (i.e. publishing on behalf of or reading latest dweets):
```
var dweetModule = require("dweetio");
var dweet = new dweetModule.Dweet();
```
**To send a message** (post a dweet), simply invoke the postDweet method, passing a JSON objet (key/value pairs) or a query string:
```
var msg = {
  "temperature": 22,
  "unit": "celcius"
 };
 
 dweetModule.postDweet(msg);
 ```
Note that you can also pass false to the postDweet method if you do not wish to received the details of the message publication result.

**To read the latest message** (read dweets), simply invoke the getLatestDweet method
```
var latestDweet = dweet.getLatestDweet();
```
**To get the list of 5 latest messagse** (list dweets), simply invoke the listLatestDweet method
```
var latestDweetList = dweet.listLatestDweets();
```
