# What is a Lead

Actually Leads and Contacts are synonyms. We use the term “Lead” in developer docs while we use “Contact” in the UI.
A Lead aggregates requests and metadata collected during conversation(s) with a single user (Anonymous or Authenticated, see next Section).
Example of metadata:
Fullname
Last name
Email
Custom metadata

In general, if the user is connected as “Anonymous” a Lead is created automatically based on the user-id (the user-id is a random generated UUID during the anonymous authentication process). All next user conversations with this UUID will be aggregated in a single Lead.

# Example

A user first will be asked for some metadata to follow up a conversation:

![image](https://user-images.githubusercontent.com/9378770/79008740-561b6680-7b5e-11ea-8d0e-3e51ac69bc08.png)

Then the user contacts the support two times, as you can see by conversations summary:

![image](https://user-images.githubusercontent.com/9378770/79008779-66cbdc80-7b5e-11ea-91c5-475c5950fdf4.png)

Now in Contacts module you can search by email (andrea1@gmail.com) for the Lead:

![image](https://user-images.githubusercontent.com/9378770/79008872-95e24e00-7b5e-11ea-8af8-3331ee479377.png)

As you can see there is only one Contact with that email. Now in contact detail you can see all the two requests made by this user:


If the user, with the same email, starts a request from another browser he will be assigned a new Anonymous user-id.
So, for example, if I made a new request from Safari (we started with Chrome browser):


As you can see the user is totally new (a new Anonymous user is created with a new UUID).
Now I insert the same email as in Chrome:



If a execute the same search as before, by email:



Now I find two Contacts, because they have a different UUID as you can see in the detail of the new Contact (Andrea Sp1):




And this user only made one conversation.

Actually we do not provide a feature to “merge” the two contacts into one (they are effectively the same user, recognized by their identical email, also if the two Contacts have different user-ids). This feature, with the ability to manually create and modify Contacts, is in the roadmap but it is not a top priority for the moment.
