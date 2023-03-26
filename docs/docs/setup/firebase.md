# Firebase

To set up your Firebase account, with Authentication and Firestore enabled:

* Create an account with Firebase (https://firebase.google.com/)
* Log into Firebase and go to the console, and click **+ Add Project**
* Give your project a name.
* When prompted for "Google Analytics for your Firebase project", make your choice as preferred. It doesn't affect Firestarter either way. If not sure, select No.
* Wait for your project to be created.

  👁️‍🗨️ When complete it says "Your new project is ready"

* Click **Continue**

  👁️‍🗨️ You are taken to the project Overview for your new project

* Click **Authentication**
* Click **Get Started**
* Click **Email/Password** under **Native Providers**
* Next to **Email/Password**, click **Enable**
* Click **Save**
* Click **Project Overview** to get back to that page again.
* Click **Cloud Firestore** 
* Click **Create Database**
* Keep the default of **Start in production mode**
* Click **Next**
* For the Location, stick with **(United States)**, unless you have a strong need to change it.
* Click **Enable**

Your Firebase is now set up for Firestarter! You will now need to get some configuration values out of it so the code can make use of this Firebase project.

* Click **Project Overview** to get back to that page again.
* Under **Get started by adding Firebase to your app**, click the Web icon that looks like **</>**.
* Give the app a nickname, e.g. Firestarter.
* Don't check **Also set up Firebase Hosting for this app**
* Click **Register App**
* Wait for registration.
* Copy the code that looks like this, and paste it into the `config.ts` file 

```javascript
// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
  authDomain: "aaaa-aaaaa.firebaseapp.com",
  projectId: "aaaa-aaaaa",
  storageBucket: "aaaa-aaaaa.appspot.com",
  messagingSenderId: "11111111111",
  appId: "1:11111111111:web:7777777777777777777777"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
```




