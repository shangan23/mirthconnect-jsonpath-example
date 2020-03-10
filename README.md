# Mirth Connect with JSON support

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
:+1: :sparkles: :camel: :tada: :rocket: :metal: :octocat:  HAPPY CODING :+1: :sparkles: :camel: :tada: :rocket: :metal: :octocat: 
