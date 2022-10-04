---
title: "Vonage CLI"
weight : 2
---

The Vonage CLI allows you to interact with your Vonage account and use our products from the command line.

## 1. Installation

```sh
npm install --location=global @vonage/cli
```

or, if using yarn:

```sh
yarn global add @vonage/cli
```

A `vonage` command is now available to use:

```sh
 vonage --help
```

## 2. Configuration

To configure the CLI to use your credentials:

```sh
vonage config:set --apiKey=xxx --apiSecret=xxx
```

The stored credentials are accessible via:

```sh
vonage config
```

> NB: Credentials are stored in `~/.config/@vonage/cli/vonage.config.json`.

## 3. Check balance

```sh
vonage balance
```

## 4. Send an SMS

The CLI has a plugin architecture so tasks for various APIs can be installed. To be able to send an SMS via the CLI, you'll need to install the sms plugin:

```sh
vonage plugins:install @vonage/cli-plugin-sms
```

We now have the `vonage sms` command - you can see how to use it:

```sh
vonage sms --help
```

To send an SMS:

```sh
vonage sms --to=15551234567 --from=Paul --message='A text message sent using the Vonage SMS API'
```

**Resources**:

- Homepage: [developer.vonage.com/application/vonage-cli](https://developer.vonage.com/application/vonage-cli)
- CLI project: [github.com/Vonage/vonage-cli](https://github.com/Vonage/vonage-cli)
