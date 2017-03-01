## __Table-of-Contents__
______
- [Tomcat](#tomcat)
- [Browser Work flow](#browserworkflow)
- [Tools](#tools)
    - [Jenkins](#tools-jenkins)
    - [CURL](#tools-curl)
    - [Heroku](#tools-heroku)
- [Python](#python)
    - [Flask](#python-flask)
- [JavaScript](#javascript)
    - [Event Handler](#javascript-eventhandler)
    - [Promise](#javascript-promise)
    - [Subscribe/Publish](#javascript-observer)
    - [JavaScript Concerns](#javascript-concerns)
    - [ExtJS Framework](#javascript-extjs)
- [Java](#java)
    - [JDBC](#java-jdbc)
    - [Hibernate](#java-hibernate)
    - [Design Pattern](#java-designpattern)
    - [Thread](#java-thread)

## Tomcat 


## BrowserWorkflow 


## Tools 


#### Tools-Jenkins 

```js
    //Run in standalone mode
    java -jar jenkins.war --httpPort=9090 //default port is 8080
```

#### Tools-CURL 

```js
    //retrieve content from internet and save to a file
    curl -o ubuntu.iso http://releases.ubuntu.com/16.04.1/ubuntu-16.04.1-desktop-amd64.iso
```

##### CURL reference 
* [comparison Table](https://curl.haxx.se/docs/comparison-table.html)
* [Curl introduction](https://curl.haxx.se/docs/httpscripting.html)

##### Tools-Heroku 
* command cheetsheet
```js
    $: heroku create
    $: git push heroku master
    
    # set up psql
    $: heroku addons:create heroku-postgresql:hobby-dev
    $: heroku config -s | grep HEROKU_POSTGRESQL

    # commonly used command
    $: heroku logs
    $: heroku pg:info
    $: heroku pg:psql
```
##### Heroku Reference
* [heroku-postgresql](https://devcenter.heroku.com/articles/heroku-postgresql#provisioning-the-add-on)

[⥣](#table-of-contents)
## Python 

```js
    #install pip
    $ sudo easy_install pip
```    

#### PythonRelatedMaterials
* [Python Quickstart](https://pip.pypa.io/en/stable/quickstart/)
* [Web Framework - Django](https://www.djangoproject.com/)
* [Web Framework - Flask (Lightweight)](http://flask.pocoo.org/)

#### Python-Flask 
* init a Flask Project 
```sh
    # install Flask
        $: mkdir FlaskAppDir
        $: virtualenv venv #create virtual environment
        $: source venv/bin/activate # activate venv
        $: pip install Flask # install Flask in the venv
```
* Flask Project Workflow
    > `Bowser` --> `routes.py` --> `templates/` --> `static/` --> `routes.py` --> `Browser`

[⥣](#table-of-contents)
## JavaScript 
#### Javascript-EventHandler 
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

#### Javascript-Promise 
> JavaScript Promises provide a mechanism for traking the state of an asynchronous task with more robustness and less chaos. 

> A Promise is a proxy for a value not neccessarily known when the promise is created. It allows you to associate handlers with an asynchronous action's eventual
success value or failure reason. This lets asynchronous methods return values like asynchronous methods: instead of immediately returning the final value, the asynchronous
method returns a promise to supply the value at some point in the future (Mozilla Foundation)

* Promise Syntax
```js
    new Promise(/* executor */ function(resolve, reject){...});
```
*  Promise states :
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

##### JavaScript promise reference
* [Promise Fundamentals 01](https://spring.io/understanding/javascript-promises) 
* [Promise Fundamentals 02](http://www.javascriptkit.com/javatutors/javascriptpromises.shtml)
* [Promise Fundamentals 03](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Promise)
* [Promise API reference](https://developers.google.com/web/fundamentals/getting-started/primers/promises#promise-api-reference)
* [Async page sample using promise](https://googlesamples.github.io/web-fundamentals/fundamentals/getting-started/primers/async-all-example.html)
* [An implementation of Promise (github lib)](https://github.com/then/promise)
* [An implementation of Promise - Lightweight (github lib)](https://github.com/stackp/promisejs)

#### Javascript-Observer
> The observer is a design pattern in which an object maintains a list of objects depending on it (observers), automatically notifying 
them of any changes to state. Sub/pub use strings to identify the event type. There is no relationship between the message and the 
target of the event. Objects are decoupled. 
> The largest benifitof uing pub/sub is the ability to break down our application into smaller, more 
loosely coupled modules. Also check [Loose coupling](https://en.wikipedia.org/wiki/Loose_coupling) for more info.

Code Sample:
```js
    globalBroadcaster.subscribe('uniqueEventName', handler);
    globalBroadcaster.publish('uniqueEventName', parameter1, parameter2,.);
    globalBroadcaster.unsubscribe('uniqueEventName', handler);
```
`Reference`: [Observer Design Pattern Reference](https://msdn.microsoft.com/en-us/magazine/hh201955.aspx)


#### JavaScript-Concerns 
1. why JavaScript is not multi-threading >> because the Javascript interpreter in the browser is a single thread.
2. What is callbakc hell and how to avoid it >> [Callback hell](http://callbackhell.com/)

[⥣](#table-of-contents)
#### JavaScript-ExtJS 
* Code Conventions
    * Code Snippet 
```js 
    Ext.define('MyApp.model.Population', {
        extend: 'Ext.data.Model',
        fields: ['year', 'population']
    });
```
    * Command line input/output exmaple

```js
    sencha generate app --ext MyApp ./MyApp
```
    * ExtJS Features
        * Cross-broswer support
        * Rich UI Components
        * Two-way binding
        * Client-side routing (used in Single-Page Application)
    * Application setup

```js
    sencha -sdk /path/to/sdk generate app MyApp /path/to/myapp 
    cd sample
    sencha app watch
```
    * Application Stytle
        * SASS (Syntactically Awesome Stylesheets) is a Stylesheet language which is heavily used in ExtJS
    
    * View Model - app.js - Starting code for ExtJS Application
        ```js
            Ext.application({
                name: 'MyApp',
                extend: 'MyApp.Application',
                requires:[
                    'MyApp.view.main.Main'
                ],
                mainView: 'MyApp.view.main.Main'
            });
        ```
    * View Model - app.js -  More in app.js file
        ```js
            Ext.define('MyApp.Application',{
                extend: 'Ext.app.Application', 
                name : 'MyApp',
                stores :[
                    //TODO: add global / shared stores here
                    // 'store' in app.js is nothing but data stores
                ],
                launch: function(){
                    //TODO - launch the application
                    // 'launch' function is defined in Ext.app.Application. 
                    // This function is called after the page is loaded
                }
            });
        ```
     * View model - MainModel.js
        ```js
            //this class is the view model for the Main view of the Application. 
            // The view model extends from Ext.app.ViewModel.
            Ext.define('MyApp.view.main.MainModel', {
                extend : 'Ext.app.ViewModel',

                alias: 'viewModel.main',

                data: {
                    name : 'MyApp',
                    ...
                }
            });
        ```
    * Controller - MainController.js

    ```js
        // you can see that onIte,Selected function is defined, this will be called when an ittem is 
        // seleceted from the grid in the view
        Ext.define('MyApp.view.main.MainController', {
            extend: 'Ext.app.ViewModel',
            alias : 'controller.main',
            onItemSelected: function(sender, record){
                Ext.Msg.confirm('Confirm', "Are you sure?', 'onConfirm', this);
            },
            onConfirm: function (choice){
                if (choice === 'yes'){
                    //
                }
            }
        });
    ```
* Sencha Cmd
    * Cmd - build the application

        ```sh
            # this will build HTML, JS ,SASS and so on, read app.json for build config
            sencha app build
        ```
    * Cmd - launch the application

        ```sh
            # 'watch' can be used to rebuild and launch the application, it can also monitor any code changes made
            sencha app watch
        ```
    * Cmd - code generation
    
        ```sh
            # using sencha cmd, you can generate the ExtJS code, such as views, controllers
            sencha generate view myApp.MyView
            sencha generate model MyModel id:int, fname, lname 
            sencha generate controller MyController
        ```

##### Ext-Core 
* Ext
    > Ext is a global singleton object that encapsulates all classes, singletons, and utility methods in the Sencha library.
* Ext - application
    * Many applications are initiated with Ext.application. This function loads the Ext.app.Application class and starts it with 
    the given configuration after the page is loaded. 
    ```js
        Ext.application({
            name: 'MyApp', // this create a global vaibale caled MyApp
            extend: 'MyApp.Application',
            launch: function(){

            }
        });
    ```

* Ext - define
    * to create or override a class, you can use this function. three parameter wil be taken (name: name of the class, data: properties to apply to this class, callback: callback function after class created)
    ```js
        Ext.define(name ,data, callback);

        Ext.define('Car', {
            name: null,
            constructor: function(name){
                if(name){
                    this.name = name;
                }
            }
        }),
        start: function(){
            alert('Car started');
        }
    ```
    * Ext.define - extend class
    ```js
        Ext.define('ElectricCar', {
            extend: 'Car',
            start: function(){
                alert("Electric car started");
            }
        });
    ```
    * Ext.define - override method
    ```js
        Ext.define('My.ux.field.Text',{
            override : 'Ext.form.field.Text',
            setValue : function(val){
                this.callParent(['In override']);
                return this;
            }
        });
    ```
    * Ext.define - create singleton class
    ```js
        Ext.define('Logger', {
            singleton: true,
            log: function(msg){
                console.log(msg);
            }
        })
    ```

* Ext - create
    * use the following signature to create an instance of a class:
        ```js
            Ext.create(Class, Options);

            // following will create an instance of the ElectricCar class 
            // and passes a value
            var myCar = Ext.create('ElectricCar', {
                name: 'MyElectricCar'
            }); 
            //if Ext.Loader is enabled. Ext.create will automatically 
            //download the appropriate JavaScript file if the ElectricCar
            //class does not exist
        ```
* Ext - onReady
    * This function is called once the page is loaded
    ```js
        Ext.onReady(function(){
            new Ext.Component({
                renderTo: document.body,
                html: 'DOM ready!'
            });
        });
    ```

* Ext - widget
    * eg: 'Ext.panel.Panel' has an alias called 'widget.panel'. Example below are equivalent
    ```js
        // example of creating an instance of Ext.panel.Panel
        Ext.create('Ext.panel.Panel', {
            renderTo: Ext.getBody(),
            title : 'Panel'
        });

        Ext.widget('panel', {
            renderTo: Ext.getBody(),
            title: 'Panel'
        });

        Ext.create('widget.panel', {
            renderTo : Ext.getBody(),
            title: 'Panel'
        });

        //usage example
        Ext.application(
            name : 'Fiddle',
            launch : function(){
                Ext.create('widget.panel', {
                    renderTo: Ext.getBody(),
                    title: 'Panel'
                });
            }
        );
    ```

* Ext.Loader
    * this is used for dynamic dependency loading. Normally, the `Ext.require` shorthand
    is used. when you define a class, it's a good practice to specify the list of components 
    required, `in this case, the required class are load asynchronously, which can improve the performance`
    as shown in the following code:
    ```js
        Ext.require(['widget.window', 'layout.border', 'Ext.data.Connection']);
        //use wildcards if you need all components/class under a particular namespace
        Ext.require(['widget.*', 'layout.*', 'Ext.data.*']);
        //exclude what is not required
        Ext.exclude('Ext.data.*').require('*');
    ```

* Ext - add listeners to an instance
    ```js
        // add a listener for the click event when the object is created
        Ext.create('Ext.Button', {
            renderTo : Ext.getBody(),
            listeners : {
                click : function(){
                    Ext.Msg.alert('Button clicked!');
                }
            }
        });

        //or add listeners after instance created
        var button = Ext.create('Ext.Button');

        button.on({
            moseover: function(){
                //do something

            }, 
            mouseover: function(){
                //do something
            }
        });
    ```

* Ext - remove listener
    > to remove the listeners, you need the reference to the function, you cannot use anonymous funciton.
    ```js
        var HandClick = funciton(){
            Ext.Msg.alert('My button clicked!');
        }

        Ext.create('Ext.Button', {
            listeners:{
                click: HandleClick
            }
        });

        button.un('click', HandleClick);
    ```

* Ext DOM accessing
    0. Access element direct through DOM tree
        ```js
            /*
                <div id="mydiv"></div>
            */
            var div  = Ext.get('mydiv');
            div.on('click', function(e, t, eOpts){
                //do something
            });
        ```
    0. Ext.get
        ```js
            //take teh ID of the DOM and retrieve the element wrapped as Ext.dom.Element 
            var mydiv = Ext.get('myDivId');
        ```
    0. Ext.query 
        ```js
            // retrieve an array of nodes using CSS class name
            var someNodes = Ext.query('.oddROw',
            myCustomComponent.getEl().dom);
        ```
    0. Ext.select 
        ```js
            // Ext.select returns a single object of type CompositeElement, that represents a 
            //collection of elements.
            var rows = Ext.select('div.row'); //Matches all divs with class row
            rows.setWidth(100); //All elements become 100 width 

            //the commands can also be chanied
            Ext.select('div.row').setWidth(100);

            //multiple selections
            Ext.select('div.row, sapn.title'); //matches all divs with class row and all spans with class title 

            // `select` take th HTML body as the root and start searching the entire DOM tree of ther body by default
            Ext.get('myEl').select('div.row');

            /* line below equivalent to line above
            this will first find the element having id 'myEl', and then under the root element. it will 
            search for 'div' tags having the class 'row'
            */
            Ext.select('div.row', true, 'myEl');

            //selection chaining
            Ext.select('div.row[title=bar]:first')
        ```
    0. Ext.Containers
        > Containers are a special type of component that are capable of holding other component. 
        Ext.container.Container is the base class of all the containers in ExtJS. Ext.toolbar.Toolbar, 
        Ext.panel.Panel, and Ext.Editor are examples. but Ext.button.Button is not capable of containing 
        since it is not derived from Ext.container.Container.

* Ext - Data Packages
    > Models, Schema, Stores, Proxies, Filtering and sorting

    * **Stores**
        > A store represents acollection of instances of the model and proxies used to get the data. 
        the store also defines collection operations, such as sorting, filtering, and so on. It is defined by 
        extending the Ext.data.Store class. Usually, when you define a store, you need to specify a proxy 
        in the store. This is a configuration that tells the store how to read and write data.

        ```js
            //this is an example of a store that uses the RESTful API request
            // to load the data in the JSON format
            var myStore = Ext.create('Ext.data.Store',{
                model: 'Emplloyee',
                storeId: 'mystore',
                proxy:{
                    type: 'rest',
                    url:'/employee',
                    reader:{
                        type: 'json',
                        rootProperty: 'data'
                    }
                },
                autoLoad: true, //the load method will be called automatically when the store is created
                autoSync: true //sync will happed as soon as you edit, add, or remove the records in the store
            }); 

            // example of a sync call
            store.sync(
                {
                    callback: function(batch, options){
                        //to do
                    },
                    success: function(batch, options){
                        // do something
                    },
                    failure: function(batch, options){
                        // do something 
                    },
                    scope: this
                }
            ); 

            // store for static data
            Ext.create('Ext.data.Store', {
                model: 'Employee',
                data:[
                    {
                        firstName: 'Shiva',
                        lastName: 'Kumar',
                        gender: 'Male',
                        fulltime: true,
                        phoneNumber: '123-456-7890'
                    }
                ]
            });

            // store - local sorting
            var myStore = Ext.create('Ext.data.Store', {
                model: 'Employee',
                sorters: [{
                    property: 'firstName',
                    direction: 'ASC'
                }, {
                    property: 'fullname',
                    direction: 'DESC'
                }],

                filters: [
                    {
                        property: 'firstName'
                        value: /an/
                    }
                ]
            });

            //accessing the store
            /*
            1. accessing the store using StoreManager
                -- using the store manager's lookup method, you can access store from anywhere in
                -- the application. 'storeId' is neeeded.
                -- Note: when the store is instanistaed by a controller, storeId will be overrided by the name of the store 
                **/
            Ext.create('Ext.data.Store', {
                model: 'Employee',
                storeId: 'mystore',
                proxy:{
                    type: 'rest',
                    url: '/employee',
                    reader: {
                        type: 'json',
                        rootProperty: 'data'
                    }
                }
            });
            Ext.data.StoreManager.lookup('myStore'); // NOTE: 'Ext.getStore' is equivalent to 'Ext.data.StoreManager.lookup

            /*
            2. access the store via the getStore method of 'Ext.app.ViewModel' when you are in the 'ViewController'
            */
            var myStore = this.getViewModel().getStore('myStore');

        ```
* Store - _Events_
    > there are multiple store events you can listen. add, beforeload, beforesync, datachanged, load, remove, update

    ```js
        // events are add to listeners, code to listen to the event listed below
        init: function(){
            this.getViewModel().getStore('myStore').on('load', this.onStoreLoad, this);
        }
    ```

* Proxies 
    * The client-side proxy
        * memory
        * LocalStorage
        * SessionStorage
    * The server-side proxy
        * Ajax: this is used to send asynchronous requests
        * Direct: this uses Ext.Direct to communicate with server
        * JSONP(JSON WITH PADDING): This is useful when you need to send a request to another domain. Ajax can be used only to send requests to the same domain
        * REST 

[⥣](#table-of-contents)
## Java 

#### Java-JDBC 
* the process to implement the JDBC
>load the driver >> make connection >> get statement object >> execute the query >> close the connection
   

#### Java-Hibernate 
* the process to implement the sessionFactory
> sessionFactory.openSession() >> session.BeginTransaction() >> session.createQuery() >> session.getTransaction.commit() >> close()

#### Java-DesignPattern 
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
#### Java-Thread 
* Thread hints
    1. join function is used to execute thread in squence (InterruptedException)
    2. lock >> separate lock for reading&writting
    3. sleep >> doesn't release lock or monitor
        wait >> need notify (release lock or monitor)
    4. deadlock >> ordered access will avoid deadlock
    5. race condition >> use synchronnized
    6. run() >> can be execute on thread object twice
        start() >> will create a new thread, can be execute once only


            
