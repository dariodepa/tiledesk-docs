
# Authentication

## Custom Authentication

The Custom JWT authentication provider allows users to authenticate with an authentication system that is independent from Tiledesk. The external system must return a signed [JSON Web Token](https://jwt.io/introduction/) that contains a unique ID value for the authenticated user.

Tiledesk uses the JWT to identify your application’s users and authenticate their requests but does not impose any restrictions on the external authentication system’s requirements or authentication methods.


## Generating a Project shared secret

To configure your widget for visitor authentication, you need a shared secret. A shared secret is a security setting, intended to be generated, copied, and pasted into a communication with your engineering team, or directly into your codebase, in a single sitting. It should not be entered into a browser.

Only Chat administrators can configure visitor authentication settings.

To generate the shared secret required for authenticated visitors

* Open the Dashboard and go to Project Name &gt; Project Settings.
* Scroll down to the Visitor Authentication section and click the Generate button.

![](https://raw.githubusercontent.com/Tiledesk/tiledesk-docs/master/docs/tiledesk-project-settings2.png)

Note:The shared secret is intended to remain secure. As a result, it will only appear in full one time. If you don’t have access to the shared secret and need the full secret to create your token, you can reset the secret by clicking the 'Generate' button. Regenerating a new shared secret will revoke the previous token. If you have concerns the shared secret has been compromised, you should regenerate a new one. If you need to rotate the keys, you should schedule it when Chat is offline because regenerating the secret cause visitors to be disconnected from the widget.


## Create a Tiledesk JWT token

You must set the following required fields of the user object :

* **\_id** is the custom unique user identifier of the external authentication system.
* **subject**. JWTs describe their subject in the sub claim. sub must be equal to value `userexternal`
* **audience**. JWTs describe their audience in the aud claim. Must be `https://tiledesk.com/projects/<YOUR_PROJECT_ID>`.

Optional fields:

* **firstname**. It's the user firstname
* **lastname**. It's the user lastname
* **other** jwt claims.

The external authentication system must create the JWT signing the user object with the project authentication secret code. See here to obtain a Project JWT Secret: [https://developer.tiledesk.com/widget/auth\#generating-a-chat-shared-secret](https://developer.tiledesk.com/widget/auth#generating-a-chat-shared-secret)

User object example:

```text
{_id: "123", firstname:"andrea", lastname:"leo", email: "email2@email.com",  customAttr: "c1", sub:  "userexternal",  aud:  "https://tiledesk.com/projects/5c81593adf767b0017d1aa68'}
```



## Generate JWT Token Server Side

Find the template below that fits your language needs. Customize the sample as needed, making sure to replace the \#{details} with your own information.

If none of these samples match your needs, JWT has a more extensive list of [JWT libraries](https://jwt.io/#libraries-io) to explore.

### NodeJS

Install [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken):

```text
npm install jsonwebtoken --save-dev
```

Then, generate a token using the shared secret:

```text
var jwt = require('jsonwebtoken'); 
var payload = {
  id: '#{customerIdentifier}',
  firstname: '#{customerFirstname}',
  lastname: '#{customerLastname}',
  email: '#{customerEmail}',  
  subject: 'userexternal',
  audience: 'https://tiledesk.com/projects/#{OUR_PROJECT_ID}',  
};
var token = jwt.sign(payload, '#{yourSecret}');
```

#### PHP

Download [PHP-JWT](https://github.com/firebase/php-jwt):

```text
composer require firebase/php-jwt
```

Generate a token using the shared secret:

```text
$payload = {
  'id' => '#{customerIdentifier}' ,
  'firstname' => '#{customerFirstname}',
  'lastname' => '#{customerLastname}',
  'email' => '#{customerEmail}',
  'subject' => 'userexternal',
  'audience'=> #{timestamp+expiration time},
  'external_id' => 'https://tiledesk.com/projects/#{YOUR_PROJECT_ID}'
};
$token = JWT::encode($payload, '#{yourSecret}');
```

