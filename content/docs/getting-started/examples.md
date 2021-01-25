---
title: "Examples"
weight: 11
description: >
  Examples of using bigbluebutton-js.
---

## API Calls

The library provides several modules. Use `api` module to construct URLs. To handle API calls, a developer should utilize `http` module.

This division into separate modules allows developers to use `bigbluebutton-js` with custom http clients (the library default one is `axios`), and xml parsers.

```javascript
const bbb = require('bigbluebutton-js')
 
// BBB_URL and BBB_SECRET can be obtained
// by running bbb-conf --secret on your BBB server
// refer to Getting Started for more information
let api = bbb.api(
    process.env.BBB_URL, 
    process.env.BBB_SECRET
  )
let http = bbb.http
 
// api module itslef is responsible for constructing URLs
let meetingCreateUrl = api.administration.create('My Meeting', '1', {
  duration: 2,
  attendeePW: 'secret',
  moderatorPW: 'supersecret',
})
 
// http method should be used in order to make calls
http(meetingCreateUrl).then((result) => {
  console.log(result)
 
  let moderatorUrl = api.administration.join('moderator', '1', 'supersecret')
  let attendeeUrl = api.administration.join('attendee', '1', 'secret')
  console.log(`Moderator link: ${moderatorUrl}\nAttendee link: ${attendeeUrl}`)
 
  let meetingEndUrl = api.administration.end('1', 'supersecret')
  console.log(`End meeting link: ${meetingEndUrl}`)
})
```

## WebHooks

This API allows third party applications to subscribe to a BBB meeting events. Events are propogated in form of HTTP POST requests. A list of events includes: a meeting was created, a user joined the meeting, a new presentation was uploaded, a user left the meeting, a recording is being processed, and some more.

WebHooks is not currently installed with BigBlueButton by default. To install it on your BBB server, run:

```bash
sudo apt-get install bbb-webhooks
```

For comprehensive WebHooks documentation, see [`docs.bigbluebutton.org`](https://docs.bigbluebutton.org/dev/webhooks.html).

```javascript
const bbb = require('bigbluebutton-js')
 
// BBB_URL and BBB_SECRET can be obtained
// by running bbb-conf --secret on your BBB server
// refer to Getting Started for more information
let api = bbb.api(
    process.env.BBB_URL, 
    process.env.BBB_SECRET
  )
let http = bbb.http
 
http(api.hooks.create('https://mysite.com/bbb/hooks'))
  .then(console.log)
  .catch(console.log)
```

On `https://mysite.com/bbb/hooks` , the following application will listen for the events:

```javascript
const express = require('express')
const app = express()
 
app.use(express.json())
app.use(express.urlencoded({ extended: true }))
 
app.post('/bbb/hooks', function (req, res) {
  let event = JSON.parse(req.body.event)
 
  // Expand json before logging it to console
  console.log(
    require('util').inspect(event, { showHidden: false, depth: null })
  )
  res.json({})
})
 
app.listen(3001)
```
