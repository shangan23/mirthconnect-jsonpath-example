# Mirth Connect with JSONPath support

This repository helps you to implement JsonPath in Mirth Connect. 

## MirthConnect Server
* Download the Jar mirth-json1.0.0.jar to MirthConnect server
* Navigate to home folder of MirthConnect
* Open custom-lib folder
* Put the downloaded mirth-json1.0.0.jar inside custom-lib folder.

## MirthConnect Administrator
* Log in to your MirthConnect Administrator.
* Click on Setting from the side window
* From the main content navigate to Resources Tab.
* Click on Reload resource from the side window.
* Click Yes on the confirmation window to let MirthConnect know mirth-json1.0.0.jar is loaded.

#### MirthConnect Channels

* Create your channel.
* Add the below code to instantiate object.
```java
var obj = new Packages.com.mirth.jsonpath.Frame();
```
## Documentation on methods and it's usage

1. The <code>MakeJson(Src,Dest,Map)</code> method will create a Json according to the mapping provided in the <code>Map</code> Json
``` javascript
obj.MakeJson(src, dest, map)
```
### Sample Implementation
``` javascript
var obj = new Packages.com.mirth.jsonpath.Frame();
var srcObj = {
    name: "John",
    age: 31,
    city: "New York"
};
var Src = JSON.stringify(srcObj);

var destObj = {
  "module": "user",
  "details": {
    "name": "",
    "age": null,
    "city": ""
  }
};
var Dest = JSON.stringify(destObj);

var mapObj = {
  "write": {
    "$.name": "$.details.name",
    "$.age": "$.details.age",
    "$.city": "$.details.city"
  }
};
var Map = JSON.stringify(mapObj);

var result = obj.MakeJson(Src,Dest,Map);
```
### Output of <code>result</code>
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
       
