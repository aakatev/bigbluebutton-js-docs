---
title: "API Reference"
weight: 5
description: >
  API reference for the BigBlueButton server.
---

When using `bigbluebutton-js` the required parameters should be passed as function arguments, while non-required can be passed as options object. 

For comprehensive API reference, see [`docs.bigbluebutton.org`](https://docs.bigbluebutton.org/dev/api.html#api-calls).

## Administration

### create - create a new meeting

Parameters

| Parameter                          | Description                                                      | Required/Otional         |
| ---------------------------------- | ---------------------------------------------------------------- | ------------------------ |
| name                               | Meeting name                                                     | required                 |
| meetingId                          | Meeting ID                                                       | required                 |
| attendeePW                         | Attendee password                                                | optional                 |
| moderatorPW                        | Moderator password                                               | optional                 |
| welcome                            | Chat welcome message                                             | optional                 |
| dialNumber                         | Cell phone access number                                         | optional                 |
| voiceBridge                        | FreeSWITCH voice conference number                               | optional                 |
| maxParticipants                    | Maximum maximum number of participants                           | optional                 |
| logoutURL                          | Redirect URL after logout                                        | optional                 |
| record                             | Enable/disable meeting record                                    | optional                 |
| duration                           | Meeting maximum duration                                         | optional                 |
| isBreakout                         | `true` for a breakout rooms                                      | required (breakout room) |
| parentMeetingID                    | Top-level meeting id of the breakout room                        | required (breakout Room) |
| sequence                           | Breakout room sequence number                                    | required (breakout Room) |
| freeJoin                           | `true` allows user to have a choice of a breakout room to join   | optional (breakout Room) |
| meta                               | Meeting metadata                                                 | optional                 |
| moderatorOnlyMessage               | Moderator only chat message                                      | optional                 |
| autoStartRecording                 | `true` will instruct to start recording on first user join       | optional                 |
| allowStartStopRecording            | Allow users to start/stop recordings                             | optional                 |
| webcamsOnlyForModerator            | Users webcams are only seeing by moderators                      | optional                 |
| logo                               | Default logo in Flash client                                     | optional                 |
| bannerText                         | Banner text                                                      | optional                 |
| bannerColor                        | Banner background color                                          | optional                 |
| copyright                          | Copyright text                                                   | optional                 |
| muteOnStart                        | Mute all users on meeting start                                  | optional                 |
| allowModsToUnmuteUsers             | Allow moderators to unmute users                                 | optional                 |
| lockSettingsDisableCam             | `true` will prevent users from sharing webcams                   | optional                 |
| lockSettingsDisableMic             | `true` will prevent users from sharing microphones               | optional                 |
| lockSettingsDisablePrivateChat     | `true` will disable private chats                                | optional                 |
| lockSettingsDisablePublicChat      | `true` will disable public chat                                  | optional                 |
| lockSettingsDisableNote            | `true` will disable notes                                        | optional                 |
| lockSettingsLockedLayout           | `true` will lock meeting layout                                  | optional                 |
| lockSettingsLockOnJoin             | `false` will disable applying settings                           | optional                 |
| lockSettingsLockOnJoinConfigurable | `true` will allow applying `lockSettingsLockOnJoin`              | optional                 |
| guestPolicy                        | Possible values: `ALWAYS_ACCEPT`, `ALWAYS_DENY`, `ASK_MODERATOR` | optional                 |

### join - join an existing meeting

Parameters

| Parameter     | Description                                                                                            | Required/Otional        |
| ------------- | ------------------------------------------------------------------------------------------------------ | ----------------------- |
| fullName      | Users full name                                                                                        | required                |
| meetingId     | Meeting ID                                                                                             | required                |
| password      | Attendee/moderator password                                                                            | required                |
| createTime    | If provided, parameter should match meeting `createTime`                                               | optional                |
| userID        | User ID                                                                                                | optional                |
| webVoiceConf  | Custom voip voice extension                                                                            | optional                |
| configToken   | Apply custom configuration associated with the token                                                   | optional                |
| defaultLayout | Layout to load on user join                                                                            | optional                |
| avatarURL     | Link to user avatar ([#8566](https://github.com/bigbluebutton/bigbluebutton/issues/8566))              | optional                |
| redirect      | Custom redirect behaviour of join API ([learn more](https://docs.bigbluebutton.org/dev/api.html#join)) | optional (experimental) |
| clientURL     | Display custom url ([learn more](https://docs.bigbluebutton.org/dev/api.html#join))                    | optional (experimental) |
| joinViaHtml5  | `true` to force HTML5                                                                                  | optional                |
| guest         | `true` for guest users                                                                                 | optional                |

### end - forcefully end an existing meeting

Parameters

| Parameter | Description        | Required/Otional |
| --------- | ------------------ | ---------------- |
| meetingId | Meeting ID         | required         |
| password  | Moderator password | required         |

## Monitoring

### isMeetingRunning - check whether a meeting is running

Parameters

| Parameter | Description | Required/Otional |
| --------- | ----------- | ---------------- |
| meetingId | Meeting ID  | required         |

### getMeetings - get the list of existing meetings

### getMeetingInfo - get details of an existing meeting

Parameters

| Parameter | Description | Required/Otional |
| --------- | ----------- | ---------------- |
| meetingId | Meeting ID  | required         |

## Recording

### getRecordings - get list of recordinngs

Parameters

| Parameter | Description                                                                                               | Required/Otional |
| --------- | --------------------------------------------------------------------------------------------------------- | ---------------- |
| meetingId | Meeting ID                                                                                                | optional         |
| recordID  | Recordings record ID                                                                                      | optional         |
| state     | Recordings state (possible values: `processing`, `processed`, `published`,`unpublished`,`deleted`, `any`) | optional         |
| meta      | Recordings metadata                                                                                       | optional         |

### publishRecordings - set publishing/unpublishing of a recording

Parameters

| Parameter | Description             | Required/Otional |
| --------- | ----------------------- | ---------------- |
| recordID  | Recordings record ID    | required         |
| publish   | `true` or `false` value | required         |

### deleteRecordings - delete an existing recording

Parameters

| Parameter | Description          | Required/Otional |
| --------- | -------------------- | ---------------- |
| recordID  | Recordings record ID | required         |

### updateRecordings - update recording metadata

Parameters

| Parameter | Description          | Required/Otional |
| --------- | -------------------- | ---------------- |
| recordID  | Recordings record ID | required         |
| meta      | Recordings metadata  | optional         |

## WebHooks

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