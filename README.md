### **Firebase Files**

Add the [manifest.json](https://github.com/BFMarks/IterableWebPush/blob/master/manifest.json) file to the route of your project.  It must be accessible from the URL, similar to this example:


![alt text](https://www.evernote.com/shard/s652/sh/71e80fd2-e3bd-4cdd-9ee6-1b9c044e4974/06a4bc0d1f94d0f8/res/1edb23f7-afc6-4c18-a50e-2596ac542e21/skitch.png)


Add the [firebase-messaging-sw.js](https://github.com/BFMarks/IterableWebPush/blob/master/firebase-messaging-sw.js) file right next to the manifest.json file.

### **Setup Project and Add Code**

1. Create your project on the [Firebase Console](https://console.firebase.google.com/).  Name your project 

2. Open the [Cloud Messaging](https://console.firebase.google.com/project/_/settings/cloudmessaging/) tab of the Firebase console Settings pane and scroll to the Web configuration section.

3. In the Web Push certificates tab, click Generate Key Pair. The console displays a notice that the key pair was generated, and displays the public key string and date added.


![image alt text](https://www.evernote.com/shard/s652/sh/ba9f21d3-276c-4005-a0c4-9245f00e120c/6d3f36ad17674500/res/07ebd49d-813a-4e15-843b-0ef3f3986af1/skitch.png)

The key pair is your Firebase webpush certificate.


4. [Add the github code](https://github.com/BFMarks/IterableWebPush/blob/master/IterableWebPush.html) to your HTML file in the <script> section

5. Change the credentials to your firebase credentials and Iterable credentials.  Don't forget the SENDER ID in the firebase-messaging-sw.js file.

6.  Add the [requestPermission() function](https://github.com/BFMarks/IterableWebPush/blob/00df3084d9912ed1d08b747dafbe591ee6dd9eb0/IterableWebPush.html#L170) to the place in your code that you want to trigger the permission popup.  Typically, it’s right after signup once you have the user email.

7.  Add the users email to the email variable

8.  Call the [deleteToken() function](https://github.com/BFMarks/IterableWebPush/blob/00df3084d9912ed1d08b747dafbe591ee6dd9eb0/IterableWebPush.html#L187) when a user refreshes the page as this will acquire the latest token and re-update it to the Iterable server.  It is recommended to put this in periodically to ensure you have the most up-to-date browser token.

9.  Got to your Iterable App and add your Server Key from Firebase.  

![image alt text](https://www.evernote.com/shard/s652/sh/49cc51f6-6287-4427-81df-8cd1fac290ba/808f7b7c2d665285/res/338c51e4-d58e-40c0-9c75-de11dd59da0d/skitch.png)



### **TESTING:**
Open the Chrome console (option+command+j), collect the current browser token from the console and add it the “Send test push” highlighted section in Iterable Integration page.  You should receive a test push on your browser.

![image alt text](https://www.evernote.com/shard/s652/sh/77b9d64a-0fce-4cc2-83c1-b1e25ceba247/d2ac17764706022c/res/e1f07c2a-e8b7-4f77-92b0-a736260efaa2/skitch.png)



### **NOTES:**

* **The webpush popup will not appear if the page is front and center.  It must be minimized or backgrounded.**

* **If the popup fails, Chrome may also need to be reset.**
