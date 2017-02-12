# All in One

## Tomcat 


## Jenkins

```sh
#Run in standalone mode
$ java -jar jenkins.war --httpPort=9090 //default port is 8080
```

## CURL
```sh
#retrieve content from internet and save to a file
$ curl -o ubuntu.iso http://releases.ubuntu.com/16.04.1/ubuntu-16.04.1-desktop-amd64.iso
```

#### CURL reference
* [comparison Table](https://curl.haxx.se/docs/comparison-table.html)
* [Curl introduction](https://curl.haxx.se/docs/httpscripting.html)


## Python
```sh
#install pip
$ sudo easy_install pip
```    
#### Python reference
* [Python Quickstart](https://pip.pypa.io/en/stable/quickstart/)
* [Web Framework - Django](https://www.djangoproject.com/)
* [Web Framework - Flask (Lightweight)](http://flask.pocoo.org/)


## JDBC
* the process to implement the JDBC
>load the driver >> make connection >> get statement object >> execute the query >> close the connection
   

## Hibernate
* the process to implement the sessionFactory
> sessionFactory.openSession() >> session.BeginTransaction() >> session.createQuery() >> session.getTransaction.commit() >> close()


## JavaScript
#### Javascript event handler
```js
//javascript event handler
element.event = function(){
                //add statements here
            };

document.getElement().addEventListener('click', function, false);

    //javascript DOM get and append elements
    function getEleFunc(){
        getElementById();
        getElementsByTagName();
        getElementsByClassName();
    }

    //append new element to exisisting element
    var newEle = document.createElement("li");
    existingEle.appendChild(newEle);
    var newTextNode = document.createTextNode("New item text");
    newEle.appendChild(newTextNode);
    
    //javascript AJAX
        var myRequest = new XMLHttpRequest();
        myRequest.onreadystagechange() = function() {
            if(myRequest.readystate === 4){
                //do append
            }
        }
        myRequest.open('GET', 'file.txt', true);
        myRequest.send(null);
```

#### Javascript Promised
> JavaScript Promises provide a mechanism for traking the state of an asynchronous task with more robustness and less chaos. 

> A Promise is a proxy for a value not neccessarily known when the promise is created. It allows you to associate handlers with an asynchronous action's eventual
success value or failure reason. This lets asynchronous methods return values like asynchronous methods: instead of immediately returning the final value, the asynchronous
method returns a promise to supply the value at some point in the future (Mozilla Foundation)

* Syntax
```js
    new Promise(/* executor */ function(resolve, reject){...});
````
* Promise states :
    * fulfilled - the action relating to the promise successed
    * rejected - the action relating to the promise failed
    * pending - hasn't fulfilled or rejected yet
    * settled - has fulfilled or rejected
* Promise fates :
    * Promises have two possible mutually exclusive fates: resolved, and unresolved.
        * A promise is resolved if trying to resolve or reject it has no effect, i.e. the promise has been "locked in" to either follow another promise, or has been fulfilled or rejected.
        * A promise is unresolved if it is not resolved, i.e. if trying to reslove or reject it will have been an impact on the promise.
        > A promise can be "resolved to" either a promise or thenable, in which case it will store the promise or thenable for later unwrapping; or it can be a non-promise value, in which case it is fulfilled with that value.

* Promise Properties
    * Promise.length >> Length property whose is always 1 (number of constructor arguments)
    * Promise.prototype >> Represents the prototype for the Promise constructor.

* how you create a promise
```js
var promise  = new Promise(function(resolve, reject){
    // do a thing, possibly async, then...
    if(/*everything turned out fine*/){
        resolve("stuff worked!");
    }
    else{
        reject(Error("it broke"));
    }
})
```
* how you use the promise
```js
promise.then(function(result){
    console.log(result); // "Stuff worked!"
}, function(err){
    console.log(err); //Error: "It broke"
});
```
> then() takes two arguments,  callback for a success case, and another for the failure case. Both are optional, so you can add a callback for the success or failure case only.
###### JavaScript promise reference
* [Promise Fundamentals 01](https://spring.io/understanding/javascript-promises) 
* [Promise Fundamentals 02](http://www.javascriptkit.com/javatutors/javascriptpromises.shtml)
* [Promise Fundamentals 03](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Promise)
* [Promise API reference](https://developers.google.com/web/fundamentals/getting-started/primers/promises#promise-api-reference)
* [Async page sample using promise](https://googlesamples.github.io/web-fundamentals/fundamentals/getting-started/primers/async-all-example.html)
* [An implementation of Promise (github lib)](https://github.com/then/promise)
* [An implementation of Promise - Lightweight (github lib)](https://github.com/stackp/promisejs)


#### JavaScript Concerns
1. why JavaScript is not multi-threading >> because the Javascript interpreter in the browser is a single thread.
2. What is callbakc hell and how to avoid it >> [Callbakc hell](http://callbackhell.com/)


## Java

#### Java Design Pattern
* Singleton
    1. used to eliminate the option of instantiating more than one object
    2. pros >> lazy initialization
               cons >> since it is used for global, it would be hard for testing
    3. getInstance() - constructor of Singleton class is private
    4. example: java runtime getRuntime()
    5. code sample
```java
        public class A{
            private static A a;
            private A(){}
            public static A getInstance(){
                if(a == null){
                    a = new A();
                }
                return a;
            }
        }
```
#### Java Thread
* Thread hints
    1. join function is used to execute thread in squence (InterruptedException)
    2. lock >> separate lock for reading&writting
    3. sleep >> doesn't release lock or monitor
        wait >> need notify (release lock or monitor)
    4. deadlock >> ordered access will avoid deadlock
    5. race condition >> use synchronnized
    6. run() >> can be execute on thread object twice
        start() >> will create a new thread, can be execute once only


            
