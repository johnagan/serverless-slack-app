![](https://camo.githubusercontent.com/547c6da94c16fedb1aa60c9efda858282e22834f/687474703a2f2f7075626c69632e7365727665726c6573732e636f6d2f6261646765732f76332e737667) ![](https://camo.githubusercontent.com/d59450139b6d354f15a2252a47b457bb2cc43828/68747470733a2f2f696d672e736869656c64732e696f2f6e706d2f6c2f7365727665726c6573732e737667)

# Serverless Slack App Template

## Install Serverless and provision AWS
1. Set-up your [AWS Credentials](./docs/providers/aws/guide/credentials.md)
2. Install [Serverless.js](https://serverless.com)

  ```
  npm install -g serverless
  ```
3. Install The Serverless Slack App Template and provision all AWS services

  ```
  serverless install --url https://github.com/johnagan/serverless-slack-app
  cd serverless-slack-app
  npm install
  serverless deploy
  ```
  ![serverless-slack-install](https://cloud.githubusercontent.com/assets/35968/21295095/49631b60-c502-11e6-9043-715fefb180df.gif)

## Create a Slack App
1. Create a new [Slack App](https://api.slack.com/apps/new)
2. Use the generated **POST** url for Slack's slash commands, events, and interactive messages
3. Update the [serverless.yml](serverless.yml) with your new Slack App keys

Slack | Serverless
:---:|:---:
![screen shot 2016-12-18 at 9 04 04 am](https://cloud.githubusercontent.com/assets/35968/21295094/49605452-c502-11e6-9d19-96680cd39858.png) | ![screen shot 2016-12-18 at 9 04 30 am](https://cloud.githubusercontent.com/assets/35968/21295097/49707ac6-c502-11e6-8a4d-ec2f35a1e744.png)

4. Run deploy again and install the App
  
  ```
  serverless deploy
  ```
  ![serverless-slack-app](https://cloud.githubusercontent.com/assets/35968/21295093/495c9b32-c502-11e6-95c4-86e0acc95296.gif)


## Install the Slack App and test
1. Goto the **GET** url provided from serverless (above)
2. Walk through the OAuth flow and install the App
3. Goto the team and test the slash command `/greet`
4. :boom:

![serverless-slack-app-install](https://cloud.githubusercontent.com/assets/35968/21295096/49648982-c502-11e6-912f-c287b82da3a1.gif)

_All the tokens and urls above were invalidated before posting this tutorial. You will need to use your own tokens to test_
