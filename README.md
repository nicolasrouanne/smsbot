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
```bash
$ yarn install
```  

You can **start your project** :rocket:
```bash
$ npm start
```

### Deployment
You can virtually deploy this _Node.js_ application anywhere you like; although here is some guides on how to deploy it on **Heroku** and **Google App Engine**.

#### Heroku
Create a **Heroku** app and deploy it (see [Deploying with git](https://devcenter.heroku.com/articles/git)).
```bash
$ git push heroku master
```


Then set your _environment variables_ in `.env` file. We will use the [`heroku-config`](https://github.com/xavdid/heroku-config) plugin to set those _environment variables_ in **Heroku**.
```bash
# install `heroku-config`
$ heroku plugins:install heroku-config
# push your config in .env to heroku
$ heroku config:push
```

#### Google App Engine
If you deploy on **_Google App Engine_**, you must specify a `app.yaml` file with all your configuration options, including _environment variables_. As this contains secrets, the `app.yaml` is not checked in source control.

A good start for an `app.yaml` file is to copy the `app.yaml.example` and replace placeholder values with your actual credentials
```bash
# copy the example app.yaml into your app.yaml file
$ cp app.yaml.example app.yaml
# edit the file and replace dummy credentials by actual ones
$ nano app.yaml
```

You need [**to set up `Google Cloud SDK`**](https://cloud.google.com/appengine/docs/flexible/nodejs/download) on your machine, as well as [**create an App Engine application**](https://cloud.google.com/appengine/docs/flexible/nodejs/managing-projects-apps-billing#create).
Then you can deploy your application
```bash
$ gcloud app deploy
```