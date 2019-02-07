**Firebase Files**

Add the [manifest.json](https://github.com/BFMarks/IterableWebPush/blob/master/manifest.json) file to the route of your project.  It must be accessible from the URL. similar to this example:

![image alt text](image_0.png)

Add the [firebase-messaging-sw.js](https://github.com/BFMarks/IterableWebPush/blob/master/firebase-messaging-sw.js) file right next to the manifest.json file.

**Setup Project and Add Code**

1. Create your project on the [Firebase Console](https://console.firebase.google.com/).  Name your project 

### 2. Open the [Cloud Messaging](https://console.firebase.google.com/project/_/settings/cloudmessaging/) tab of the Firebase console Settings pane and scroll to the Web configuration section.

3. In the Web Push certificates tab, click Generate Key Pair. The console displays a notice that the key pair was generated, and displays the public key string and date added.

![image alt text](image_1.png)

The key pair is your Firebase webpush certificate.

4. [Add the github code](https://github.com/BFMarks/IterableWebPush/blob/master/IterableWebPush.html) to your HTML file in the <script> section

5. Change the credentials to your firebase credentials and Iterable credentials

6.  Add the [requestPermission() function](https://github.com/BFMarks/IterableWebPush/blob/00df3084d9912ed1d08b747dafbe591ee6dd9eb0/IterableWebPush.html#L170) to the place in your code that you want to trigger the permission popup.  Typically, it’s right after signup once you have the user email.

7.  Add the users email to the email variable

8.  Call the [deleteToken() function](https://github.com/BFMarks/IterableWebPush/blob/00df3084d9912ed1d08b747dafbe591ee6dd9eb0/IterableWebPush.html#L187) when a user refreshes the page as this will acquire the latest token and re-update it to the Iterable server.  It is recommended to put this in periodically to ensure you have the most up-to-date browser token.

**NOTES:**

* **The webpush popup will not appear if the page is front and center.  It must be minimized or backgrounded.**

* **If the popup fails, Chrome may also need to be reset.**
