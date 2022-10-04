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
npm install express dotenv --save
```

- `express` - a minimal and flexible Node.js web application framework
- `dotenv` - loads environment variables from a `.env` file into `process.env`

You will also install [nodemon](https://nodemon.io/), a utility that will monitor for any changes in your source and automatically restart your server.

```sh
npm install --location=global nodemon
```


## 2. Express app

Next, create the environment file `.env` and the entry point for the app `index.js`:

```sh
touch .env
touch index.js
```

Add the following to `index.js`:

```js
const express = require('express');
const app = express();
const port = 8662;

app.get('/', (req, res) => {
  res.send('Hello World');
});

app.listen(port, () => {
  console.log(`Server started at http://localhost:${port}`);
});
```

Now, you are ready to launch the server via `nodemon`:

```sh
nodemon index.js
```

A start message will be displayed:

```text
Server started at http://localhost:8662
```

Notice the port is `8662`. You will that in the next step.

## 3. Make your app accessible to the world

You will be building some endpoints that you will use as webhooks for your Vonage application (we're going to create on the next page). For this to work, the endpoints will need to be available to the Vonage server to read data from and push data to.

[localtunnel])(https://github.com/localtunnel/localtunnel) is a utility that exposes your localhost to the world for easy testing. In another terminal window:

```sh
npm install --location=global localtunnel
```

And make a local port available via a `loca.lt` subdomain - for example:

```sh
lt --port 8662 --subdomain "your-subdomain"
```

Now, you can load your local website via `https://your-subdomain.loca.lt` (or equivalent).

**Resources**:

- Express: [expressjs.com](https://expressjs.com/)
- nodemon: [nodemon.io](https://nodemon.io/)
- localtunnel: [github.com/localtunnel/localtunnel](https://github.com/localtunnel/localtunnel)
