RingCentral Webhooks Demo in JavaScript with Express
====================================================

## Overview

This is a quick webhooks demo that runs using JavaScript, Node.js and Express with the [RingCentral JavaScript SDK](https://github.com/ringcentral/ringcentral-js) v2.x

## Installation

### Via NPM

```bash
$ git clone https://github.com/grokify/ringcentral-demos-webhooks
$ cd ringcentral-demos-webhooks/javascript-express
$ npm install
```

## Configuration

### Your Host

When configuring this demo app, you will need an Internet accessible webserver to host your webhook since the RingCentral service will need to be able to reach it. You can either use your own publicly available webserver or, for development purposes, you can use a tunneling service like [ngrok](https://ngrok.com/) which will redirect both https and http to your localhost system.

### Config File

Edit the `.env` file to add your application key and application secret.

```bash
$ cd ringcentral-demos-webhooks/javascript-express
$ cp config-sample.env.txt .env
$ vi .env
```

Some properties of note:

| Property | Description | 
|----------|-------------|
| `RC_APP_REDIRECT_URL` | This is the OAuth 2.0 redirect URL, this will end in `/call` and be something like `http://localhost:8080/callback` or `https://755c8b38.ngrok.io/callback`. This needs to be configured in your app in the Developer Portal(https://developers.ringcentral.com) |
| `MY_APP_WEBHOOK_URL` | This is the webhook URL which ends in `/hook` and can be something like `http://localhost:8080/hook` or `https://755c8b38.ngrok.io/hook`. |

In the [Developer Portal](http://developer.ringcentral.com/), ensure the redirect URI in your config file has been entered in your app configuration. By default, the URL is set to the following for this demo:

### TLS / SSL

The example server can also run using TLS / SSL if you have a certificate. If you are testing locally, you can use `ngrok`'s HTTPS endpoint to point to your non-secure server, however, if you are hosting this online, this can run TLS directly. To do this, set the following config parameters:

| Property | Description |
|----------|-------------|
| `MY_APP_TLS_ENABLED` | Set to `1` for HTTPS and `0` for HTTP |
| `MY_APP_TLS_PRIVATE_KEY` | Set to path to PEM file for private key |
| `MY_APP_TLS_CERTIFICATE` | Set to path to PEM file for certificate |

## Usage

Open the web page:

```bash
$ npm start
```

Go to the URL (you must start ngrok if using it):

```
https://755c8b38.ngrok.io/
````

Then click the <input type="button" value="Login with RingCentral"> button to authorize the demo app and view the access token.
