---
title: "Getting Started"
weight : 1
---

In this section, you will get familiar with the Vonage APIs.

## Requirements

Before being able to make an API call, you need to have signed up for a [Vonage Developer Account](https://dashboard.nexmo.com).

![Dashboard](/intro/dashboard.png)

## API Key and Secret

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