# Widget Authentication

## Enabling authenticated visitors

Require Widget Javascript API v4

### Overview

You can configure your widget to authenticate visitors using the Javascript API and JWT token.

When you configure the Chat widget to use authenticated visitors, you get the following benefits:

* Ability to have higher confidence and security that the visitor/customer you or your agents are talking to is the real deal
* Support for cross device/browser identification. The visitor can be viewed as the same person if or when they choose to use a different device or browser when the custom ID is specified in the authentication call.

To configure your widget for visitor authentication, you need to [Generate a Project Shared Secret](../apis/authentication/README.md#generating-a-project-shared-secret).
Only Chat administrators can configure visitor authentication settings.
Once you have generated the shared secret, use it to create a JWT token that you'll add to your Web Widget snippet.

### Creating a JWT token

To create a JWT token and add the code to the Chat snippet

1\) Construct a server-side payload of data for the JWT token. Your token needs to be dynamically generated from the server-side on page load. Please follow this guide to [Create a JWT Token](../apis/authentication/README.md). 


2\) Use the **window.tiledesk.signInWithCustomToken** Javascript API to provide a function which supplies a fresh JWT every time it is invoked. Below is a code example:

```text
window.tiledesk.signInWithCustomToken("<JWT JWT_TOKEN_HERE_GENERATED_SERVER_SIDE>");
```

Example:

```text
window.tiledesk.signInWithCustomToken("JWT 12345678...");
```

See an [example here](https://www.w3schools.com/code/tryit.asp?filename=GEWSE8JKG2QI).



## About the agent experience with authenticated visitors

A few things are updated in the Chat dashboard when an agent starts chatting with an authenticated visitor.

First, the agent will be able to tell the visitor is authenticated by the authenticated checkmark overlay on the visitor's avatar.

![](https://raw.githubusercontent.com/Tiledesk/tiledesk-docs/master/docs/authuser.png)

