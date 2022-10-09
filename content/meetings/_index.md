---
title: "Meetings API"
weight : 6
---

The Meetings API allows you to integrate real-time, high-quality interactive video meetings into your web apps. It is ideal for those who want plug and play meetings with limited customization; it takes only a few lines of code to generate a meeting and embed it into your application.

As it is currently in Beta, it has not been added to the Server SDKs, so you will have to use the API directly.

## Interface

The Meeting section consists of one screen that the *curl* command to use to create a room with the name "EDC 2022".

![Make Call](/meetings/interface.png?classes=thumbnail_lg)

## Code Structure

All code required for this section is contained in the **_meetings** folder of the app:

- **_meetings/index.js** - displays the template below
- **_meetings/index.mustache** - the Meetings page

![Messages code](/meetings/code.png?classes=thumbnail_lg)

## Endpoints

The 5 endpoints in use are:

| HTTP Method | Path                   | Purpose                        |
| ----------- | ---------------------- | ------------------------------ |
| GET         | **/meetings**          | place call form                |
| POST        | **/meetings/rooms**    | rooms webhook                  |
| POST        | **/meetings/sessions** | event webhook                  |

## Resources

- Documentation : https://developer.vonage.com/meetings
- API Reference: https://developer.vonage.com/api/meetings
- Create an Instant Room: https://developer.vonage.com/meetings/code-snippets/create-instant-room
