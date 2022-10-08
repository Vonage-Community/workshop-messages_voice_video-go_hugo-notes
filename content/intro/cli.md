---
title: "Vonage CLI"
weight : 2
---

The Vonage CLI allows you to interact with your Vonage account and use our products from the command line.

## 1. Installation

It can be installed via **npm**:

```sh
npm install --location=global @vonage/cli
```

or, if using yarn:

```sh
yarn global add @vonage/cli
```

The **vonage** command is now available to use:

```sh
 vonage --help
```

---

## 2. Configuration

Before using the CLI, it needs to be configured with your credentials:

```sh
vonage config:set --apiKey=$VONAGE_API_KEY --apiSecret=$VONAGE_API_SECRET
```

The stored credentials are accessible via:

```sh
vonage config
```

> NB: Credentials are stored in **~/.config/@vonage/cli/vonage.config.json**.

---

## 3. Check balance

To check your account balance:

```sh
vonage balance
```

---

## 4. Send an SMS

The CLI has a plugin architecture so tasks for various APIs can be installed. To be able to send an SMS via the CLI, you'll need to install the sms plugin:

```sh
vonage plugins:install @vonage/cli-plugin-sms
```

We now have the **vonage sms** command - you can see how to use it:

```sh
vonage sms --help
```

To send an SMS, copy the snippet below and replace **YOUR_NUMBER** with your mobile number:

```sh
vonage sms --message='A text message sent using the Vonage CLI' --from=Vonage --to=YOUR_NUMBER
```

---

**Resources**:

- Homepage: [developer.vonage.com/application/vonage-cli](https://developer.vonage.com/application/vonage-cli)
- CLI project: [github.com/Vonage/vonage-cli](https://github.com/Vonage/vonage-cli)
