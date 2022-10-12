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

### 2.1 Local webpage

You can now navigate to [http://localhost:3000](http://localhost:3000) to see the app running:

![Workshop app](/intro/app.png)

## 3. Environment Variables

The app will be using your Vonage credentials. A sample file **env.sample** is provided - you will create a copy named **.env**:

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

You will be adding your credentials to this file in the next step.

## 4. Make your app accessible to the world

For some operations, Vonage will require some information for you - this is done via [webhooks](https://en.wikipedia.org/wiki/Webhook). Similarly, when an event happens, Vonage will send that event information to a webhook URL you will be providing.

Here is what happens when you receive a inbound message via the Messages API:

![Receiving an SMS](/messages/inbound_url.gif?classes=thumbnail_lg)

The app you just cloned includes the required endpoints but they will need to be available to the Vonage server to read data from and push data to.

ngrok is the programmable network edge that adds connectivity, security, and observability to your apps with no code **changes**. Installation guides and downloadable archives are available at [https://ngrok.com/download](https://ngrok.com/download).

### 4.1 ngrok subdomain

Assuming that you downloaded the right ngrok package for your platform and placed it in your home directory, open a new terminal window or tab and launch it:

```sh
~/ngrok http 3000
```

### 4.2 Public webpage

Your local app is now available via **https://random_subdomain.ngrok.io**. 

ngrok also provides a local monitoring server at <http://localhost:4040> to inspect, replay, and modify your requests. It is a great way to visualise incoming webhooks events.

## Addendum: firewalls & networks

Various utilities exist to enable you to expose local ports to the world. Two are described below (ngrok preferred).

Some corporate networks are more restrictive than others - please contact your IT support for alternatives to the tools described below.

### ngrok

ngrok is the programmable network edge that adds connectivity, security, and observability to your apps with no code **changes**

It is a commercial product with additional features, such as reserving a subdomain, available with a subscription.

### localtunnel

[localtunnel](https://github.com/localtunnel/localtunnel) is a utility that exposes your localhost to the world for easy testing. In another terminal window:

```sh
npm install --location=global localtunnel
```

And make a local port available via a **loca.lt** subdomain - for example:

```sh
lt --port 3000 --subdomain "your-subdomain"
```

Now, you can load your local website via **https://your-subdomain.loca.lt** (a random subdomain will be used if the one you specified is not available).

> NB: At times, you might not be able to reuse a subdomain on a short notice. A random one will be provided instead.

### Alternatives

Various cloud-based alternative exist and could we used to spin un the app. 

#### Github Codespaces

![Github Codespaces](/intro/github_codespaces.png?classes=thumbnail_lg)

#### Stackblitz

![Stackblitz](/intro/stackblitz.png?classes=thumbnail)
![Stackblitz Project](/intro/stackblitz_project.png?classes=thumbnail)

## Resources

- Express: [expressjs.com](https://expressjs.com/)
- nodemon: [nodemon.io](https://nodemon.io/)
- [ngrok](https://ngrok.com/)
- localtunnel: [github.com/localtunnel/localtunnel](https://github.com/localtunnel/localtunnel)
