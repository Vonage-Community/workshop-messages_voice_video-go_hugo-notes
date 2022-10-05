---
title: "Workshop App"
weight: 3
---

Throughout this workshop, you will be building various functionality as part of a Node Express app. We'll start by setting it up.

## 1. Node Project

In the terminal, create and navigate to a folder that will host your server - use a folder named `workshop` in a location of your choice and make a note of it:

```sh
mkdir workshop
cd workshop
```

Next step is to initialise the application:

```sh
npm init -y
```

... and add couple of libraries to the app:

```sh
npm install express mustache-express dotenv @vonage/server-sdk --save
```

- **express** - a minimal and flexible Node.js web application framework
- **mustache-express** - enables the use of mustache, a template engine, with express
- **dotenv** - loads environment variables from a *.env* file into *process.env*
- **@vonage/server-sdk** - the Vonage Node Server SDK

You will also install [nodemon](https://nodemon.io/), a utility that will monitor for any changes in your source and automatically restart your server.

```sh
npm install --location=global nodemon
```

## 2. Express app

Next, create the environment file **.env**, a **public** folder for resources and the entry point for the app **server.js**:

```sh
touch .env
mkdir views
touch server.js
```

Add the following to **server.js**:

```js
'use strict';

require('dotenv').config();

const Vonage = require("@vonage/server-sdk");
const vonage = new Vonage({
  apiKey: process.env.API_KEY,
  apiSecret: process.env.API_SECRET,
  applicationId: process.env.APP_ID,
  privateKey: process.env.PRIVATE_KEY
});

const express = require('express');
const app = express();
const port = 3000;

app.use(express.static("public"));

app.use(express.json());
app.use(express.urlencoded({ extended: true }));

var mustacheExpress = require('mustache-express');
app.engine('mustache', mustacheExpress());
app.set('view engine', 'mustache');
app.set('views', __dirname + '/views');

// utility - print request to console
var showRequest = (req, res) => {
  console.log('-----------------------');
  console.log(`URL: ${req.protocol}://${req.get('host')}${req.originalUrl}`);
  console.log(req.body);
  console.log('-----------------------');
  res.status(200).end();
}

// Homepage
app.get('/', (req, res) => {
  res.send('Hello World');
});

// Messages - status webhook

// Messages - inbound webhook

// Messages - form

// Messages - send SMS

// Start the server
app.listen(port, () => {
  console.log(`Server started at http://localhost:${port}`);
});

```

Now, you are ready to launch the server via `nodemon`:

```sh
nodemon -e js,mustache server.js
```

A start message will be displayed:

```text
Server started at http://localhost:3000
```

Notice the port is **3000**. You will that in the next step.

## 3. Make your app accessible to the world

You will be building some endpoints that you will use as webhooks for your Vonage application (we're going to create on the next page). For this to work, the endpoints will need to be available to the Vonage server to read data from and push data to.

[localtunnel])(https://github.com/localtunnel/localtunnel) is a utility that exposes your localhost to the world for easy testing. In another terminal window:

```sh
npm install --location=global localtunnel
```

And make a local port available via a **loca.lt** subdomain - for example:

```sh
lt --port 3000 --subdomain "your-subdomain"
```

Now, you can load your local website via **https://your-subdomain.loca.lt** (or equivalent).

**Resources**:

- Express: [expressjs.com](https://expressjs.com/)
- nodemon: [nodemon.io](https://nodemon.io/)
- localtunnel: [github.com/localtunnel/localtunnel](https://github.com/localtunnel/localtunnel)
