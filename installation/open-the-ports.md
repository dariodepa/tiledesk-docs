# Open the firewall ports

Tiledesk  installation requires the following ports to be open:

* 80: Nginx proxy service. 443 for https. 
* 3000: Tiledesk server service
* 4040: Ngrok service. Ngrok is required only if you don't have a public ip for the tiledesk server \(local development installation\). 
* 4200: Web Widget UI
* 9005: Firebase CLI service. Required only for the installation steps. 
* 5000: Firebase CLI service. Required only for the installation steps.
* 8080: Web Ionic UI . This is optional because you have to access to Web Ionic UI through the Nginx proxy.
* 4500: Tiledesk Dashboard UI. This is optional because you have to access to Tiledesk Dashboard UI through the Nginx proxy.

![](../.gitbook/assets/image%20%286%29.png)

