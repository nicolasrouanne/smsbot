# SMS Bot
## TL;DR
SMS Bot is an application to send and receive SMS (text messages) in Slack.

> **Credits**: it is greatly inspired by [`TalkBot`](https://github.com/slackapi/TalkBot) by **SlackApi** (_Slack Dev Team_)

## Setup pre-requisites
You need to create a **Slack application** that users will be able to add to their workspace. This setup process will provide you credentials for `smsbot`.

### Slack
- [Create](https://api.slack.com/apps) a new **Slack application**
> You should retrieve the following credentials
```
SLACK_CLIENT_ID=<your-client-id>
SLACK_CLIENT_SECRET=<your-client-secret>
SLACK_VERIFICATION_TOKEN=<your-verification-token>
```
- [Add](https://api.slack.com/bot-users#setup) a **Bot User**, for instance `smsbot`
- **Add the Bot to your team**, by clicking on _Install App_. You should be provided with 2 tokens for your bot, the _OAuth Access Token_ and the _Bot User OAuth Access Token_.
```
SLACK_BOT_TOKEN=xoxb-<your token>
SLACK_AUTH_TOKEN=xoxp-<your token>
```

- Add **permissions scope** to your bot. Into _OAuth & Permissions > Scopes_ add the following scopes
  - `bot` - _Add a bot user with the username @smsbot_
  - `channels:read` - _Access information about user’s public channels_
  - `chat:write:bot` - _Send messages as SmsBot_
  - `im:read` - _Access information about user’s direct messages_
  - `im:write` - _Modify user’s direct messages_

### First run
You should know have a complete `.env` file. Install the dependencies:
```
$ yarn install
```  

You can **start your project** :rocket:
```
$ npm start
```