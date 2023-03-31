# Firebase

!!! note

    These steps require that you already have the source code. If not then [get the source code](getthecode.md) first

To set up your Firebase account, with Authentication and Firestore enabled:

* Create an account with Firebase (https://firebase.google.com/)
* Log into Firebase and go to the console, and click **+ Add Project**
* Give your project a name.
* When prompted for "Google Analytics for your Firebase project", make your choice as preferred. It doesn't affect Firestarter either way. If not sure, select No.
* Wait for your project to be created.

!!! info

    When complete it says "Your new project is ready"

* Click **Continue**

!!! info

    You are taken to the project Overview for your new project

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
* Select the "Config" radio box
* Check that the code has a single variable `const firebaseConfig` and no other code. (See example below)
* 
```typescript
const firebaseConfig = {
  apiKey: "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
  authDomain: "aaaa-aaaaa.firebaseapp.com",
  projectId: "aaaa-aaaaa",
  storageBucket: "aaaa-aaaaa.appspot.com",
  messagingSenderId: "11111111111",
  appId: "1:11111111111:web:7777777777777777777777"
};
```

* In the box showing the code, like this, click the copy icon.
* Replace the existing `const firebaseConfig` statement in `nextjs/src/firebase/config.ts`, with the one you copied.
* The `config.ts` file should look like this now:

```typescript
const firebaseConfig = {
  apiKey: "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
  authDomain: "aaaa-aaaaa.firebaseapp.com",
  projectId: "aaaa-aaaaa",
  storageBucket: "aaaa-aaaaa.appspot.com",
  messagingSenderId: "11111111111",
  appId: "1:11111111111:web:7777777777777777777777"
};

export default firebaseConfig;
```

* Check that the project builds correctly with this change:
    * On the command line, change directory into the `nextjs` folder.
    * Run `yarn build`.
    * Check that there are no errors.
    * If there are errors, double check you have pasted correctly. 
    * If there are still errors you can raise an [issue on Github](https://github.com/mcapodici/firestarter/issues) and I will help as soon as I can.


