---
title: "WebHooks Reference"
weight: 6
description: >
  WebHooks reference for the BigBlueButton server.
---

For comprehensive WebHooks reference, see [`docs.bigbluebutton.org`](https://docs.bigbluebutton.org/dev/webhooks.html#registering-hooks-api-calls).

### create - create a new hook

Parameters

| Parameter   | Description                         | Required/Otional |
| ----------- | ----------------------------------- | ---------------- |
| callbackURL | Callback URL to receive events      | required         |
| meetingID   | Meeting ID                          | optional         |
| getRaw      | `true` set events to be unprocessed | optional         |

### destroy - remove an existing hook

Parameters

| Parameter | Description | Required/Otional |
| --------- | ----------- | ---------------- |
| hookID    | Hooks ID    | required         |

### list - list existing hooks

Parameters

| Parameter | Description | Required/Otional |
| --------- | ----------- | ---------------- |
| meetingID | Meeting ID  | optional         |