---
description: >-
  This guide is still in beta. The docker images is nightly build so can
  contains bugs and instability.
---

# Running Tiledesk with Docker Compose

Note that you need to know a bit of [Docker](https://docs.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) to follow these instructions.

Tiledesk uses [Chat21](http://www.chat21.org) as messaging platform. Refer to [Architecture overview](../../architecture/schema.md) to undestand the product's modules.

**Please help us improving this documentation**: if you encounter a problem, something you don’t understand or a typo, use [this link](https://github.com/Tiledesk/tiledesk-server/issues) to ask a question. You could also open a PR to directly fix the documentation on Github, if you want.


Tiledesk Installation
from source code


Applicable to Tiledesk version 1

Tiledesk uses Chat21 as messaging platform. Refer to Architecture overview to understand the product's modules.

Tiledesk is composed by the following components:
tiledesk-server
tiledesk-dashboard
chat21-cloud-functions
chat21-web-widget
chat21-ionic
Installation tips
Enable https to front-end and backend endpoints. https is required for push notifications
Create a DNS entries for:
tiledesk-server. Create a DNS entry like api.YOURDOMAIN.COM. Configure a virtualhost for it.
chat21-web-widget. Create a DNS entry like widget.YOURDOMAIN.COM. 
tiledesk-dashboard and chat21-ionic. Create a DNS entry like support.YOURDOMAIN.COM. You must be able to access :
/dashboard -> Tiledesk dashboard component
/chat -> Chat21 ionic component
Install the latest stable release version of the components. Check the last release under Releases tab on Github page of every components.
Create and configure a Firebase project
Sign up on Firebase and create a project. Please refer to our guide or directly to Firebase https://firebase.google.com to accomplish and better understand this task.
Install chat21-cloud-functions
To install chat21-cloud-functions follow this README: https://github.com/chat21/chat21-cloud-functions
tiledesk-server 
Download the tiledesk-server source code from github or from a private repo (for Enterprise version).
Follow this guide: https://github.com/Tiledesk/tiledesk-server/blob/master/README.md#install-from-source-code
Configure the support module of  chat21-cloud-functions 
Follow this guide:
https://github.com/chat21/chat21-cloud-functions/blob/master/docs/setup_options.md#support-mode

tiledesk-dashboard
Follow this guide to install and configure Tiledesk-Dasboard: https://github.com/Tiledesk/tiledesk-dashboard
chat21-web-widget
Follow this guide to install and configure the Web Widget:
https://github.com/chat21/chat21-web-widget


Configure push notification
Follow this guide to configure push notification for chat21-cloud-functions: https://github.com/chat21/chat21-cloud-functions/blob/master/docs/setup_options.md#push-notification
Configure Chat21-ionic following this guide: https://github.com/chat21/chat21-ionic#push-notification






```text
docker-compose run server nano ./confenv/.env
```

Open the the following URL:

{% embed url="https://localhost/dashboard" caption="" %}

