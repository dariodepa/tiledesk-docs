---
description: >-
  Dialogflow external chatbot with explicit human handoff using user intent
---

# Dialogflow  Tutorial 4 - Explicit Human handoff with user intent

## Introduction

In the previuos tutorial we learned how to automatically switch to a human agent based on the number of consecutive fallbacks during a conversation.

What if you want the user to explicitly choose to switch to a human conversation?

In this case the simplest thing that you need to do is starting from any of the above tutorials, adding a specific intent do Dialogflow that will switch to a human agent.

## Train the 'talk to agent' intent

Open your Agent's Dialogflow console. Add a new intent. Let's call this intent 'talk to human'.
We'll train this intent with a single phrase (more phrases can be added as a convenience).

#picture intent train

Now the event will reply with:

'I'm putting you in touch with an operator' \agent

As soon as this phrase reaches Tiledesk he automatically will remove the chatbot, adding a human operator following the rules you set in the Routing section or in the specific department.

But what happens if, while you switch to the human operator, your support team is outside of operating hours? The request will be placed in the unserved queue and will became served as soon as your team became available again. Meanwhile you should notice to the user that the the request will be taken in some hours, or probably the day after. So, simply telling "I'm putting you in touch with an operator" is not enough.

How to write a message that depends by operating hours? Simply you can mix Dialogflow messages _fulfillment_ and Tiledesk APIs to reach your goal.

# Replying with a message depending by operating hours

# enable webhook
# activate fulfillment on the webhook
# use the already provided webhook
# little explanation of the webhook code


