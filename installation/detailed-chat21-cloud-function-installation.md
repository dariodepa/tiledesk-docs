# Detailed Chat21 Cloud Functions installation

Authenticate to Firebase running :

```text
$ firebase login
```

![](../.gitbook/assets/image%20%2859%29.png)

![](../.gitbook/assets/image%20%2839%29.png)

If you are installing Tiledesk not in localhost change the firebase redirect url to your server ip. Change from localhost:9005?state=....... to &lt;YOUR\_IP&gt;:9005?state=......

![](../.gitbook/assets/image%20%2843%29.png)

Select the firebase project where you want to install Chat21 Cloud Functions

```text
$ firebase use --add
```

![](../.gitbook/assets/image%20%283%29.png)

Specify an alias for the firebase project \(Example test\)

![](../.gitbook/assets/image%20%2817%29.png)

Deploy the Chat21 Cloud Functions:

```text
$ firebase deploy
```

![](../.gitbook/assets/image%20%2833%29.png)

Exit from the Chat21 Cloud Functions CLI with :

```text
$ exit
```

