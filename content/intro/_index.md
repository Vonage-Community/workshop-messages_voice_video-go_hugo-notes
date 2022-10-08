---
title: "Getting Started"
weight : 1
---

In this section, you will get familiar with the Vonage APIs.

Before being able to make an API call, you need to have signed up for a [Vonage Developer Account](https://dashboard.nexmo.com).

Your API Key and Secret are available on your [Dashboard](https://dashboard.nexmo.com) under the [API Settings section](https://dashboard.nexmo.com/settings).

We will set them up as environment variables in your terminal to use them in API requests:

```sh
export VONAGE_API_KEY=""
export VONAGE_API_SECRET=""
```

To check they are set correctly:

```sh
echo $VONAGE_API_KEY
```

and

```sh
echo $VONAGE_API_SECRET
```

---

## Sections

* [Making simple API calls](/intro/api_calls)
* [Using the Vonage CLI](/intro/cli)
* [Setup the Workshop App](/intro/workshop_app)
* [Creating your Vonage App](/intro/vonage_app)