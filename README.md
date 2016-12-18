![](https://camo.githubusercontent.com/547c6da94c16fedb1aa60c9efda858282e22834f/687474703a2f2f7075626c69632e7365727665726c6573732e636f6d2f6261646765732f76332e737667) ![](https://camo.githubusercontent.com/d59450139b6d354f15a2252a47b457bb2cc43828/68747470733a2f2f696d672e736869656c64732e696f2f6e706d2f6c2f7365727665726c6573732e737667)

# Serverless Slack App Template

## Quick Start
1. Create a new [Slack App](api.slack.com/apps/new)
2. Set-up your [AWS Credentials](./docs/providers/aws/guide/credentials.md)
3. Install [Serverless.js](https://serverless.com)

  ```
  npm install -g serverless
  ```
4. Install The Serverless Slack App Template

  ```
  serverless install --url https://github.com/johnagan/serverless-slack-app
  cd serverless-slack-app
  npm install
  ```
5. Update the [serverless.yml](serverless.yml) with your new Slack App keys
6. Provision all AWS services and deploy your App to Lambda to get the urls for Slack
  
  ```
  serverless deploy
  ```
7. Use the generated **GET** url for Slack's OAuth callback and to install the App
8. Use the generated **POST** url for Slack's slash commands, events, and interactive messages
9. Run deploy again and install the App
  
  ```
  serverless deploy
  ```
10. Test the App by running `/greet`
