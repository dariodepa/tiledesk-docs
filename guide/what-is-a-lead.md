# What is a Lead

## What is a Lead

Actually Leads and Contacts are synonyms. We use the term “Lead” in developer docs while we use “Contact” in the UI. A Lead aggregates requests and metadata collected during conversation\(s\) with a single user \(Anonymous or Authenticated, see next Section\). Example of metadata: Fullname Last name Email Custom metadata

In general, if the user is connected as “Anonymous” a Lead is created automatically based on the user-id \(the user-id is a random generated UUID during the anonymous authentication process\). All next user conversations with this UUID will be aggregated in a single Lead.

## Example

A user first will be asked for some metadata to follow up a conversation:

![image](https://user-images.githubusercontent.com/9378770/79008740-561b6680-7b5e-11ea-8d0e-3e51ac69bc08.png)

Then the user contacts the support two times, as you can see by conversations summary:

![image](https://user-images.githubusercontent.com/9378770/79008779-66cbdc80-7b5e-11ea-91c5-475c5950fdf4.png)

Now in Contacts module you can search by email \(andrea1@gmail.com\) for the Lead:

![image](https://user-images.githubusercontent.com/9378770/79008872-95e24e00-7b5e-11ea-8af8-3331ee479377.png)

As you can see there is only one Contact with that email. Now in contact detail you can see all the two requests made by this user:

![image](https://user-images.githubusercontent.com/9378770/79009036-f07baa00-7b5e-11ea-9ba6-5934d77948ea.png)

If the user, with the same email, starts a request from another browser he will be assigned a new Anonymous user-id. So, for example, if I made a new request from Safari \(we started with Chrome browser\):

![image](https://user-images.githubusercontent.com/9378770/79009132-1f921b80-7b5f-11ea-9371-cc72d6e2656b.png)

As you can see the user is totally new \(a new Anonymous user is created with a new UUID\). Now I insert the same email as in Chrome:

![image](https://user-images.githubusercontent.com/9378770/79009152-2d47a100-7b5f-11ea-9317-6bfbfd14f424.png)

If a execute the same search as before, by email:

![image](https://user-images.githubusercontent.com/9378770/79009190-3d5f8080-7b5f-11ea-992e-ac49385357c6.png)

Now I find two Contacts, because they have a different UUID as you can see in the detail of the new Contact \(Andrea Sp1\):

![image](https://user-images.githubusercontent.com/9378770/79009217-523c1400-7b5f-11ea-886f-6de4336dd69d.png)

And this user only made one conversation.

Actually we do not provide a feature to “merge” the two contacts into one \(they are effectively the same user, recognized by their identical email, also if the two Contacts have different user-ids\). This feature, with the ability to manually create and modify Contacts, is in the roadmap but it is not a top priority for the moment.

