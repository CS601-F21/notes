Accessing the Slack API
=======================

These are very brief instructions for what you will need to do to access the Slack API. Refer to the documentation for complete detail.

- Your program will need to act as a client of the [Slack API](https://api.slack.com/web).

- Make sure you have read the resource: [Building Slack Apps](https://api.slack.com/start/building)

- You will need to [Create a Slack App](https://api.slack.com/apps/new). Name your app "project3-&lt;your github username&gt;" (e.g., project3-srollins).

- Your app will be a Bot. You need to grant permission for your bot to access channels:history and chat:write using Features > Oath & Permissions > Scopes > Add an OAuth Scope. 

- Next, Install App to Workspace in Settings > Basic Information.

- You will need the OAuth Token found under Features > OAuth & Permissions.

- In the Slack desktop app, add your app and make sure to add it to the channel where you will post.

- You will now be able to send `POST` requests in JSON format to `api/chat.postMessage`. You will need to specify the `Authorization` header to `Bearer you_token`  and `Content-Type: application/json; utf-8`. Your JSON body will include properties `channel` and `text`.
