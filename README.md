# Mirth Connect with JSONPath support

This repository helps you to implement JsonPath in Mirth Connect. 

## MirthConnect Server
* Download the Jar mirth-jsonpath1.1.0.jar to MirthConnect server
* Navigate to home folder of MirthConnect
* Open custom-lib folder
* Put the downloaded mirth-jsonpath1.1.0.jar inside custom-lib folder.

## MirthConnect Administrator
* Log in to your MirthConnect Administrator.
* Click on Setting from the side window
* From the main content navigate to Resources Tab.
* Click on Reload resource from the side window.
* Click Yes on the confirmation window to let MirthConnect know mirth-jsonpath1.1.0.jar is loaded.

#### MirthConnect Channels

* Create your channel.
* Add the below code to instantiate object to Core and Json for <code>Insert, Update and Delete Json</code>
``` javascript
var coreObj = new Packages.com.mirth.jsonpath.Core();
```
* Add the below code to instantiate object to Frame Json for <code>Create/Update/Read and Listing</code> with your application
``` javascript
var frameObj = new Packages.com.mirth.jsonpath.Frame();
```
## Documentation on methods and it's usage

* [Core Class - JSON Manipulation](#core-methods-for-json-manipulation)
⋅⋅⋅ [Insert]()
⋅⋅⋅ [Update]()
⋅⋅⋅ [Delete]()
⋅⋅⋅ [Read]()
* [Frame Class - Frame JSON](#)
⋅⋅⋅ [MakeJson]()

### Core Methods for JSON manipulation
#### <code>read(String json, String path)</code> method
``` javascript
coreObj.read(json, path);
```
##### Sample Implementation
``` javascript
var coreObj = new Packages.com.mirth.jsonpath.Core();
var jsonObj = {
  "module": "user",
  "details": {
    "name": "John",
    "age": 31,
    "city": "New York"
  }
};
var json = JSON.stringify(jsonObj);
var result = coreObj.read(json, "$.details.name")
```
##### Output of <code>result</code>
``` json
John
```
#### <code>insert(String json, String path, String key, String value)</code> method
``` javascript
coreObj.insert(json, path, key, value);
```
##### Sample Implementation
``` javascript
var coreObj = new Packages.com.mirth.jsonpath.Core();
var jsonObj = {
  "module": "user",
  "details": {
    "name": "John",
    "age": 31,
    "city": "New York"
  }
};
coreObj.insert(json, "$", "fullname", "Shankar Ganesh Jayaraman")
var result = coreObj.read(json, "$")
```
##### Output of <code>result</code>
``` json
{
  "module": "user",
  "details": {
    "name": "John",
    "age": 31,
    "city": "New York"
  },
  "fullname": "Shankar Ganesh Jayaraman"
}
```
#### <code>insertObject(String json, String path, String key, Object value)</code> method
``` javascript
coreObj.insertObject(json, path, key, value);
```
##### Sample Implementation
``` javascript
var coreObj = new Packages.com.mirth.jsonpath.Core();
var jsonObj = {
  "module": "user",
  "details": {
    "name": "John",
    "age": 31,
    "city": "New York"
  }
};
var obj = {};
obj.fname = "Shankar";
obj.mname = "Ganesh";
obj.lname = "Jayaraman";
var json = JSON.stringify(jsonObj);
coreObj.insertObject(json, "$", "fullname", obj)
var result = coreObj.read(json, "$")
```
##### Output of <code>result</code>
``` json
{
  "module": "user",
  "details": {
    "name": "John",
    "age": 31,
    "city": "New York"
  },
  "fullname": {
    "fname": "Shankar",
    "mname": "Ganesh",
    "lname": "Jayaraman"
  }
}
```
#### <code>update(String json, String key, String value)</code> method
``` javascript
coreObj.update(json, key, value);
```
##### Sample Implementation
``` javascript
var coreObj = new Packages.com.mirth.jsonpath.Core();
var jsonObj = {
  "module": "user",
  "details": {
    "name": "John",
    "age": 31,
    "city": "New York"
  }
};
var json = JSON.stringify(jsonObj);
coreObj.update(json, "$.details.name","Shankar")
var result = coreObj.read(json, "$.details.name")
```
#### Output of <code>result</code>
``` json
Shankar
```
#### <code>delete(String json, String path)</code> method
``` javascript
coreObj.delete(json, path);
```
##### Sample Implementation
``` javascript
var coreObj = new Packages.com.mirth.jsonpath.Core();
var jsonObj = {
  "module": "user",
  "details": {
    "name": "John",
    "age": 31,
    "city": "New York"
  }
};
var json = JSON.stringify(jsonObj);
coreObj.delete(json, "$.details.name")
var result = coreObj.read(json, "$")
```
##### Output of <code>result</code>
``` json
{
  "module": "user",
  "details": {
    "age": 31,
    "city": "New York"
  }
}
```

### Frame Methods for JSON framing
#### <code>MakeJson(String src, String dest, String map)</code> method 
``` javascript
frameObj.MakeJson(src, dest, map);
```
##### Sample Implementation
``` javascript
var frameObj = new Packages.com.mirth.jsonpath.Frame();
var srcObj = {
    name: "John",
    age: "31",
    city: "New York"
};
var Src = JSON.stringify(srcObj);

var destObj = {
  "module": "user",
  "details": {
    "name": "",
    "age": "",
    "city": ""
  }
};
var Dest = JSON.stringify(destObj);

var mapObj = {
  "write": {
    "$.details.name":"$.name",
    "$.details.age":"$.age",
    "$.details.city":"$.city" 
  }
};
var Map = JSON.stringify(mapObj);
var result = frameObj.MakeJson(Src,Dest,Map);
```
##### Output of <code>result</code>
``` json
{
  "module": "user",
  "details": {
    "name": "John",
    "age": 31,
    "city": "New York"
  }
}
```

:+1: :sparkles: :camel: :tada: :rocket: :metal: :octocat:  HAPPY CODING :octocat: :metal: :rocket: :tada: :camel: :sparkles: :+1:
       
