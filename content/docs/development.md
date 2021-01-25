---
title: "Development"
weight: 70
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

For comprehensive configuration documentation, see [our Getting Started section](https://aakatev.github.io/bigbluebutton-js-docs/docs/getting-started/).

Make sure, you have installed development dependencies. Now you can run tests:

```bash
npm run test
```