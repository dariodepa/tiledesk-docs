# Create a Firebase project

## **Create a project**

**Step 1 :** Go to[ Firebase.com](https://firebase.google.com/)

**Step 2 :** If you have a Firebase account, **Sign in**, else **create an account**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//1895b736e5.png)

**Step 3 :** Click on **Get Started**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//189642da3a.png)

**Step 4 :** Click on **Create a Project**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//1897120deb.png)

**Step 5 :** Enter **Project name** and **tick mark the checkbox** to accept Firebase terms.

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//19941c7ca1.png)

**Step 6 :** Click on **Continue**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//199509ae27.png)

## **Create an app**

**Step 7:** Click on **Add Firebase to your web app**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//1905cea821.png)

**Step 12 :** Enter **App nickname**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//1564098589.png)

**Step 13 :** Click on **Register app**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//15650377fe.png)

**Step 14 :** Here is your **apiKey, authDomain and** databaseURL.

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//179943a7c0.png)

## **Create a realtime database**

**Step 15 :** Click on **Database**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//19079e53e9.png)

**Step 16 :** In **Real time Database ,** Click on **Create database**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//5130c6436.png)

**Step 17 :** Click on **Enable**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//514afeff3.png)

## **Create a Storage**

**Step 19:** Click on **Storage** from left menu

**Step 20:** click on **Get Started**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//50259aa1c.png)

**Step 21:** Click on **Next.**

**Set as public access like this:**

```text
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read, write
    }
  }
}
```

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//1998685d59.png)

**Step 22 :** Click on **Done**

![](https://snappy.appypie.com/ckeditor/plugins/imageuploader/uploads/faqs//1999ecc634.png)

## **Create an SDK Firebase admin account**

**Step 23 :** Go to **project setting**

![](../.gitbook/assets/image%20%2880%29.png)

**Step 24 :** Under on **Service Account** tab, click on **Generate new private key** button

![](../.gitbook/assets/image%20%2877%29.png)

**Step 25**. Open the private key with a text editor and **view the parameters**

## **Get the Cloud Function URL**

**Step 26**. Under **Functions** tab get the **Chat21 Cloud Function URL**

![](../.gitbook/assets/image%20%2810%29.png)

## Enable Anonymous authentication

**Step 27** Under Authentication menu enable Anonymous authentication.

![](../.gitbook/assets/image%20%281%29.png)

