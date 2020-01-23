# Running Tiledesk from Source Code

Applicable to Tiledesk version 2

Tiledesk uses [Chat21](http://www.chat21.org) as messaging platform. Refer to [Architecture overview](../architecture/schema.md) to undestand the product's modules.

Chat21 relies on Firebase as the backend, so it's really important for you to acquire familiarity with Firebase and all of his services.

**Please help us improving this documentation**: if you encounter a problem, something you don’t understand or a typo, use [this link](https://github.com/Tiledesk/tiledesk-server/issues) to ask a question. You could also open a PR to directly fix the documentation on Github, if you want.

Tiledesk is composed by the following components:

* tiledesk-server
* tiledesk-dashboard
* chat21-cloud-functions
* chat21-web-widget
* chat21-ionic

## Installation tips

* Enable https to front-end and backend endpoints. Https is required for receiving web push notifications;
* Create a DNS entries for:
  * tiledesk-server. Create a DNS entry like this: api.YOURDOMAIN.COM. Then configure a virtualhost for it.
  * chat21-web-widget. Create a DNS entry like widget.YOURDOMAIN.COM. 
  * tiledesk-dashboard and chat21-ionic are suggested to by under the same domain to share the authentications tokens. Create a DNS entry like support.YOURDOMAIN.COM. You must be able to access :
    * /dashboard -&gt; Tiledesk dashboard component
    * /chat -&gt; Chat21 ionic component
  * Install the latest stable release versions of the components. Check the last release under Releases tab of every Github components pages.

## Overview

Please follow this guide in order to install all the Tiledesk components.

## 1. Create and configure a Firebase project

Sign up on Firebase and create a project. Please refer to our [guide](create-a-firebase-project.md) or directly to Firebase [https://firebase.google.com](https://firebase.google.com) to accomplish and better understand this task.

## 2. Install chat21-cloud-functions

To install and configure chat21-cloud-functions follow this README: [https://github.com/chat21/chat21-cloud-functions](https://github.com/chat21/chat21-cloud-functions)

Also you can find useful information regarding chat21-cloud-functions [here](detailed-chat21-cloud-function-installation.md).

## 3. Run tiledesk-server 

To install tiledesk-server version 2 please use the **dev** branch of Github and follow this guide: [https://github.com/Tiledesk/tiledesk-server/tree/dev\#install-from-source-code](https://github.com/Tiledesk/tiledesk-server/tree/dev#install-from-source-code)

## 4. Configure the webhook module of  chat21-cloud-functions

Follow this guide: [https://github.com/chat21/chat21-cloud-functions/blob/master/docs/setup\_options.md\#support-mode](https://github.com/chat21/chat21-cloud-functions/blob/master/docs/setup_options.md#support-mode)

## Install and configure tiledesk-dashboard component

Follow this guide to install and configure Tiledesk-Dasboard: [https://github.com/Tiledesk/tiledesk-dashboard](https://github.com/Tiledesk/tiledesk-dashboard)

## chat21-web-widget

Follow this guide to install and configure the Web Widget: [https://github.com/chat21/chat21-web-widget](https://github.com/chat21/chat21-web-widget)

## Configure push notification

Follow this guide to configure push notification for chat21-cloud-functions: [https://github.com/chat21/chat21-cloud-functions/blob/master/docs/setup\_options.md\#push-notification](https://github.com/chat21/chat21-cloud-functions/blob/master/docs/setup_options.md#push-notification) Configure Chat21-ionic following this guide: [https://github.com/chat21/chat21-ionic\#push-notification](https://github.com/chat21/chat21-ionic#push-notification)

```text
docker-compose run server nano ./confenv/.env
```

