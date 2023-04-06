# App Configuration (Firebase)

You will now need to get some configuration values out of it so the code can make use of this Firebase project:

* Log into your Firbease account, and go to the console.
* Click your project.
* Under **Get started by adding Firebase to your app**, click the Web icon that looks like `</>`.
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

* Commit the changes on `main` and push to Github.
  
[Vercel Account >>>](vercel-account.md){ .md-button }