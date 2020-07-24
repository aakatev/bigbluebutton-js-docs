---
title: "Development"
weight: 7
description: >
  This is the section for developers interested to contribute to the library
---

## Checkout Source

The most recent version is available on GitHub:

```bash
git clone https://github.com/aakatev/bigbluebutton-js
```

## Running Tests

To run the test suites some prior configuration is required. We use [`dotenv`](https://www.npmjs.com/package/dotenv) to manage environmental configuration. 

First, create a `.env` file in library root. The file should have the following content:

```
BBB_URL=https://mysite.com/bigbluebutton
BBB_SECRET=MySuperSecretSharedToken
```

For comprehensive configuration documentation, see [our Getting Started section](https://docs.bigbluebutton.org/2.2/install.html#bbb-installsh/).

Make sure, you have installed development dependencies. Now you can run tests:

```bash
npm run test
```