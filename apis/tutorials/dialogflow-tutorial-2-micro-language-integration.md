---
description: >-
  This tutorial shows how to easily embed buttons (or images) in your Dialogflow
  replies
---

# Dialogflow Tutorial 2 - Buttons and images

We'll start from Dialogflow Tutorial 1, just adding a small library to our original endpoint.

Follow all the steps in Tutorial 1 but stop to deploy and run the project on Heroku.

## Fork the tutorial code

You must use the code in Tutorial 1. The code is available on Github [here](https://github.com/Tiledesk/tiledesk-dialogflow-proxy-tutorial).

**Fork the tutorial** code using the Fork button. Now you have a copy of the tutorial on your own repo.

## Step 1

This time we'll give a try to the second end point already embedded into the nodeJS app: **/microlang-bot**

First we need to create a Dialogflow agent. Then we can just focus on the defaultWelcomeIntent to show how buttons and images work. This same logic will also apply to every other intent in the Dialogflow agent.

Choose the defaultWelcomeIntent and move to the 'responses' section. Remove all other responses, because we only want one welcome message from our Agent. Edit the response as the following with a copy & paste:

![image](https://user-images.githubusercontent.com/32564846/79048582-7c084000-7c1e-11ea-8b56-9375033d7930.png)

With micro language it's sufficient that you place a '\*' followed by the button text on the end of the response. You must place every button on a new line.




