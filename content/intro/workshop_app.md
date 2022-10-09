---
title: "Workshop App"
weight: 3
---

Throughout this workshop, you will be get to try various Vonage APIs - for this, a Node Express app has been built ready for you to use.

## 1. Clone Project

In the terminal, navigate to a folder of your choosing and clone the project:

```sh
git clone https://github.com/Vonage-Community/workshop-verify_messages_voice_meetings-node_express-app.git
```

Next step is to move into the project folder and install its dependencies:

```sh
cd workshop-verify_messages_voice_meetings-node_express-app
npm install
```

The app includes the following libraries:

- **express** - a minimal and flexible Node.js web application framework
- **mustache-express** - enables the use of mustache, a template engine, with express
- **dotenv** - loads environment variables from a *.env* file into *process.env*
- **cookie-parser** - adds ability to save, retrieve and delete cookies
- **@vonage/server-sdk** - the Vonage Node Server SDK

## 2. Run the project

In order to avoid having to restart your server when the project changes, you will install [nodemon](https://nodemon.io/), a utility that will monitor for any changes in your source and automatically restart your server:

```sh
npm install --location=global nodemon
```

To start the app:

```sh
nodemon -e js,mustache server.js
```

You can now navigate to [http://localhost:3000](http://localhost:3000) to see the app running:

![Workshop app](/intro/app.png)

## 3. Environment Variables

The app will be using your Vonage credentials - they will be stored in a file named **.env** inside the root of the project. A sample file **env.sample** is provided and we'll make a copy of it:

```sh
cp env.sample .env
```

Your .env file will contain the following:

```sh
# Your Vonage API key
API_KEY=''
# Your Vonage API secret
API_SECRET=''
# Your Vonage number
VONAGE_NUMBER=''
# Your Vonage Application ID
APP_ID=''
# Path to your Vonage Application private key
PRIVATE_KEY='private.key'
```

We will be adding them in the next step.

## 4. Make your app accessible to the world

For some operations, Vonage will require some information for you - this is done via [webhooks](https://en.wikipedia.org/wiki/Webhook). Similarly, when an event happens, Vonage will send that event information to a webhook URL you will be providing.

The app you just cloned includes ndpoints that can be use as webhooks for your Vonage application. For this to work, the endpoints will need to be available to the Vonage server to read data from and push data to.

### 4.1 Firewalls & networks

Various utilities exist to enable you to expose local ports to the world. Two are described below.

For the purpose of this workshop, we're going to assume that is not possible and instead you will be using custom webhooks provided by an separate application we built for this purpose.

> TODO: add URL for the repo

### 4.2 ngrok

ngrok is the programmable network edge that adds connectivity, security, and observability to your apps with no code **changes**

Installation guides and downloadable archives are available at [https://ngrok.com/download](https://ngrok.com/download).

Assuming that you downloaded the right package for your platform and placed it in your directory, to use it:

```sh
~/ngrok http 3000
```

Your local app is now available via **https://random_subdomain.ngrok.io**. It also provides a web interface at [http://localhost:4040/](http://localhost:4040/) to inspect, replay, and modify your requests.

> ngrok is a commercial product and additional features are available (such as reserving a subdomain).

### 4.3 localtunnel

[localtunnel](https://github.com/localtunnel/localtunnel) is a utility that exposes your localhost to the world for easy testing. In another terminal window:

```sh
npm install --location=global localtunnel
```

And make a local port available via a **loca.lt** subdomain - for example:

```sh
lt --port 3000 --subdomain "your-subdomain"
```

Now, you can load your local website via **https://your-subdomain.loca.lt** (a random subdomain will be used if the one you specified is not available).

## Resources

- Express: [expressjs.com](https://expressjs.com/)
- nodemon: [nodemon.io](https://nodemon.io/)
- [ngrok](https://ngrok.com/)
- localtunnel: [github.com/localtunnel/localtunnel](https://github.com/localtunnel/localtunnel)
