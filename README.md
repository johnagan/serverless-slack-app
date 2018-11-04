![](https://camo.githubusercontent.com/547c6da94c16fedb1aa60c9efda858282e22834f/687474703a2f2f7075626c69632e7365727665726c6573732e636f6d2f6261646765732f76332e737667) ![](https://camo.githubusercontent.com/d59450139b6d354f15a2252a47b457bb2cc43828/68747470733a2f2f696d672e736869656c64732e696f2f6e706d2f6c2f7365727665726c6573732e737667)

# Serverless Slack App Boilerplate
Create a serverless Slack App with AWS Lambda, API Gateway, DynamoDB, and CloudFormation. All services will be automatically provisioned for you. All that's needed is your Slack App keys.


## Install Serverless and provision AWS
![serverless-slack-install](https://cloud.githubusercontent.com/assets/35968/21295095/49631b60-c502-11e6-9043-715fefb180df.gif)
  
1. Setup your [AWS Credentials](https://github.com/serverless/serverless/blob/master/docs/providers/aws/guide/credentials.md)
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


## Create a Slack App
![serverless-slack-app](https://cloud.githubusercontent.com/assets/35968/21295093/495c9b32-c502-11e6-95c4-86e0acc95296.gif)

1. Create a new [Slack App](https://api.slack.com/apps/new)
2. Use the generated **POST** url for Slack's slash commands, events, and interactive messages
3. Update the [serverless.yml](serverless.yml) with your new Slack App keys

[Slack](https://api.slack.com/apps) | [Serverless](serverless.yml)
:---:|:---:
![slack-app-keys](https://cloud.githubusercontent.com/assets/35968/21295094/49605452-c502-11e6-9d19-96680cd39858.png) | ![serverless-keys](https://cloud.githubusercontent.com/assets/35968/21295097/49707ac6-c502-11e6-8a4d-ec2f35a1e744.png)



## Install the Slack App and Test
![serverless-slack-app-install](https://cloud.githubusercontent.com/assets/35968/21295096/49648982-c502-11e6-912f-c287b82da3a1.gif)

1. Deploy the changes to AWS `serverless deploy`
2. Navigate to the **GET** url provided from serverless
3. Walk through the OAuth flow and install the App
4. Goto the team and test the slash command `/greet`

## Update the Code
```javascript

// Slash Command handler
slack.on('/greet', (msg, bot) => {
  let message = {
    text: "How would you like to greet the channel?",
    attachments: [{
      fallback: 'actions',
      callback_id: "greetings_click",
      actions: [
        { type: "button", name: "Wave", text: ":wave:", value: ":wave:" },
        { type: "button", name: "Hello", text: "Hello", value: "Hello" },
        { type: "button", name: "Howdy", text: "Howdy", value: "Howdy" },
        { type: "button", name: "Hiya", text: "Hiya", value: "Hiya" }
      ]
    }]
  };

  // ephemeral reply
  bot.replyPrivate(message); 
});


// Interactive Message handler
slack.on('greetings_click', (msg, bot) => {
  let message = { 
    // selected button value
    text: msg.actions[0].value 
  };  

  // public reply
  bot.reply(message);
});
```
1. Open [the bot source code](src/index.js)
2. Add/Remove/Update the code with your bot functionality
3. Run `serverless deploy` to deploy your changes to AWS
4. Rinse and repeat.

_All the tokens and urls above were invalidated before posting this tutorial. You will need to use your own tokens_
