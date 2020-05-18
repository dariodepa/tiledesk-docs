
# Authentication

## Custom Authentication

The Custom JWT authentication provider allows users to authenticate with an authentication system that is independent from Tiledesk. The external system must return a signed [JSON Web Token](https://jwt.io/introduction/) that contains a unique ID value for the authenticated user.

Tiledesk uses the JWT to identify your application’s users and authenticate their requests but does not impose any restrictions on the external authentication system’s requirements or authentication methods.

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

