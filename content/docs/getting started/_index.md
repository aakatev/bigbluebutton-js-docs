---
title: "Getting Started"
weight: 2
description: >
  This page tells you how to get started with the bigbluebutton-js, including installation and basic configuration.
---

## Prerequisites

### Node

You need a recent version (10 or newer is recommended) of Node installed locally.

For comprehensive Node documentation, see [`nodejs.org`](https://nodejs.org/en/).

### BigBlueButton Server

You need a 2.2.x or 2.3.x version of BigBlueButton server server running. There are multiple ways to deploy the server, depending on your needs.

For comprehensive BigBlueButton documentation, see [`docs.bigbluebutton.org`](https://docs.bigbluebutton.org/2.2/install.html#bbb-installsh/).

## Installation

Using npm:

```bash
npm i bigbluebutton-js
```

## Configuration

You will need to provide BigBlueButton URL and secret to the script. You can obtain them by logging into you BBB server, and running:

```bash
bbb-conf --secret
```

Use the obtained values in your script:

```javascript
const bbb = require('bigbluebutton-js')
let api = bbb.api(
    process.env.BBB_URL, 
    process.env.BBB_SECRET
  )
```

Provide values to the script using environmntal variables:

```sh
BBB_URL=YOUR_URL BBB_SECRET=YOUR_SECRET node script.js
```

Alterantively, you can use [`dotenv`](https://www.npmjs.com/package/dotenv) file.