![](https://img.shields.io/badge/status-review-orange.svg)

# Node - Week 1

---

**Teaching this lesson?**

Read the Mentors Notes [here](./mentors.md)

---

## Contents

- [What is a server?](#what-is-a-server)
- [Node and its ecosystem](#node-and-its-ecosystem)
- [Express](#express)
- [Routing](#Routing)

---

## What is a server?

Servers are computer programs that receive requests from other programs, the
_clients_ and send back a response e.g share data, information or hardware and
software resources.

### ...and what is a server in plain English?

A server is a computer program. Its job is to send and receive data.

Let's take a website for example. A website is just a collection of HTML and CSS
files, images, maybe some javascript files. When you type a website address in
your browser's address bar, the browser (client) sends a **request** to the
server that lives at that address. The browser asks the server to give it the
files it needs to display the website properly. Another client can be a mobile application.

![Server flow](https://files.gitter.im/heron2014/FiiK/server.png)

## Node and its ecosystem

> [Node.js®](https://nodejs.org/en/) is a **JavaScript runtime** built on
> Chrome's **V8 JavaScript engine**. Node.js uses an **event-driven**,
> **non-blocking** I/O model that makes it lightweight and efficient.

### What is it used for?

- web servers, so creating dynamic websites
- set up a local web development environment
- easier to build desktop applications with Electron: Slack, Visual Code, Atom
- some of the biggest companies use Node.js in production: Netflix, Walmart,
  IBM, etc.

### What is the difference between javascript in a browser and Node?

- Javascript is a popular programming language and it runs in any web browser with a good web browser.
- JavaScript is mainly used for the client-side activity for one particular web application. Some of these activities can be dynamic page display in some schedule time interval, addressing business validation or basic Ajax call kind of task.
- Node.js is an interpreter and environment for the JavaScript with some specific useful libraries which JS programming can be used separately.
- Node.js can connect to other Internet Services: send emails, create communications in other protocols, etc.
- Node.js is mainly used for running or accessing any operating system for the non-blocking operation. Like:
- executing or creating a shell script
- access to the hardware, for example the hard disk

```js
const fs = require('fs');
fs.writeFileSync('hello.txt', 'Hey!!');
```

#### Exercise: Running in node

> Create a Javascript and run the last code, what happens?

### A simple Node.js server

This app starts a server and listens on port 3000 for connections. The app responds with “Hello World!” for requests,
set a **port** for our server to listen to. Think of a port as a door number; any requests that come to the server will come via
that door. Setting a port will allow us to find where our server is running.

```js
const http = require("http");
const server = http.createServer(function (req, res) {
    res.end("Hello World!");
});
server.listen(3000);
console.log("Node.js web server at port 3000 is running..");
```

The example above is actually a working server: Go ahead and click on the URL shown. You’ll get a response, with real-time logs on the page, and any changes you make will be reflected in real time.


```js
const http = require("http");
const server = http.createServer(function (req, res) {
    if (req.url === "/") {
        console.log("Main page requested at " + Date());
        res.end("Hello World");
    } else if (req.url === "/weather") {
        console.log("Migracode page requested at " + Date());
        res.end("The weather is 24.5!")
    }
});
```


## Express

[Express](http://expressjs.com/) is one of the most widely-used frameworks for
Node.js. It simplifies base features of Node.js, making it easier and faster to
build your application's backend. Learning Express gives you a great foundation
for becoming a Node.js developer.



### Hello world example

```js
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
    console.log("a client connected to the endpoint /");
    res.send('Hello World!');
})

app.listen(port, () => console.log(`Example app listening at http://localhost:${port}`))
```

This app starts a server and listens on port 3000 for connections. The app responds with “Hello World!” for requests to the root URL (/) or route. For every other path, it will respond with a 404 Not Found.

To initialise our server, we just need to call the `express()` function. This
will create an Express application for us to work with.

We use the **`app.listen`** method to do this. This method takes two arguments:
a **port** and a **callback function** telling it what to do once the server is
running. Need clarification? Read more about the `app.listen` method in the
[Express documentation](https://expressjs.com/en/4x/api.html#app.listen).

When a request reaches the server, we need a way of responding to it. In comes
the handler function. The handler function is just a function which receives
requests and handles them, hence the name.

The handler function always takes a `request` and `response` object, and sends
the response back to the client along with some information. You can decide what
to send back in your response.

#### Exercise: Running a Server locally
  
  > [1] First create a directory named myapp to hold your application, and make that your working directory:

```js
$ mkdir myapp
$ cd myapp
```

  > [2] Make a package.json file. The package.json file is easy to create from the command line. Type the following command into your terminal to get started:

```js
$ npm init
```

  > This command will initialise a step-by-step process for creating the package.json. It will ask you a bunch of questions.

> You can skip most of the questions but change the `entry point` from
> `(index.js)` to `server.js`.

> The wizard asks you for the following information: `name`, `version`,
> `description`, `main`, `test`, `repository`, `keywords`, `author`, `license` -
> do you understand all of them?

  > At the endo of the wizard, you should see a new file called `package.json` in
your project's folder.

  > Here is an example `package.json` file for a project called [Passport](https://github.com/jaredhanson/passport/blob/master/package.json).

> [3] Before we write any code, you'll need to install the Express library. 

> As we install Express, we'll need to update the `package.json` to add Express as
a dependency. We do this so that other people working on the project will know
to install Express before running any of the code. This can be done by adding
**`--save`** to the end of your command.

> Run the following command in your terminal:

```sh
npm install express --save
```

> Express should now be installed. Check your `package.json` file to make sure it
has been added as a dependency. It will look like this:

![package.json screenshot](https://cloud.githubusercontent.com/assets/10683087/16382664/be35f0b4-3c79-11e6-82b6-ae9e4a037c3f.png)

> [4] In the myapp directory, create a file named server.js and copy in the code from the example above.

> [5] Run the app with the following command:

```js
$ node app.js
```

> [6] Then, load http://localhost:3000/ in a browser to see the output of the browser and the terminal


## Routing 

Routing refers to determining how an application responds to a client request to a particular endpoint, which is a URI (or path) and a specific HTTP request method (GET, POST, and so on).

### What is an endpoint?

An endpoint is the part of the URL which comes after `/`. For example:
`/products` is the "products" endpoint. It's the URL to which you send a
request.

### What is URL?

![URL structure](../assets/http1-url-structure.png "URL")

### A server with different endpoints

We're going to try sending different responses at different endpoints. Remember
the `app.get()` method? To set up routing in your server, we just need to repeat
this method with different endpoints.

For example:

```js
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
    console.log("a client connected to the endpoint /");
    res.send('Hello World!');
})

app.get('/weather', (req, res) => {
    console.log("a client requested the weather");
    res.send('The weather is 24.5!')
}) 

app.listen(port, () => console.log(`Example app listening at http://localhost:${port}`))
```

Each route can have one or more handler functions, which are executed when the route is matched.

Route definition takes the following structure:

```js
app.METHOD(PATH, HANDLER)
```

Where:

- app is an instance of express.
- METHOD is an HTTP request method, in lowercase.
- PATH is a path on the server.
- HANDLER is the function executed when the route is matched.


#### Exercise: Add an enpoint

> Add some code so that your server sends one message when the
> endpoint is `/cities`.

### Reading endpoint parameters 

- http://localhost:3000/weather/Valencia
- https://app.slack.com/client/TMSJ4SYVD/D010G6978CC/thread/CU83UPAQH-1583245406.004600

```js
app.get('/weather/:cityName', (req, res) => {
    const name = req.params.cityName;
    console.log("a client request the weather of " + name);
    res.send('The weather in ' + name +  ' is 24.5!')
}) 
```

### Reading endpoint query 

- http://localhost:3000/weather?name=Valencia
- https://music.youtube.com/watch?v=0aJVOz5rilY&list=RDMMpsK9eOtj2ms

```js
app.get('/weather', (req, res) => {
    const name = req.query.name;
    console.log("a client request the weather of " + name);
    res.send('The weather in ' + name +  ' is 24.5!')
}) 
```

#### Exercise: make a calculator
> Make a calculator adding an endpoint for each operation [Add,Substract,Multiply,Divide], each endpoint will receive two numbers and return the result

### Responding objects

A server can respond text, HTML, but also JSON objects

```js
app.get('/weather/:cityName', (req, res) => {
    const name = req.params.cityName;
    console.log("a client request the weather of " + name);
    let city = {
        cityName: name, 
        weather:24.5
    };
    res.send(city)
}) 
```


### Logger

Adding this logger to your server, will log in the console all the requests

```js
const myLogger = (req, res, next) => {
  const visitTime = new Date();
  console.log(`visited ${req.url} at ${visitTime.toLocaleString()}`);
  next();
};
app.use(myLogger);
```

#### Exercise: Use logger
> Put the logger in your server and see the results


{% include "./homework.md" %}

