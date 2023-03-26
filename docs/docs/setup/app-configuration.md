# App Configuration

## Firebase

* Log into Firebase and go to the console, and click the project you created earlier.
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




