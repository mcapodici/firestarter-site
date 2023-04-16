# New Bot Save

The New Bot form now looks very pretty (opinions may differ!), but it does nothing. We will add the saving code using the helper functions in Firestarter.

## Magic CRUD helpers in Firestarter

In the file `IBackend.ts` we define the interface for our backend, which is a class that talks to Firebase to store data and do authentication.

Within this there are some functions for helping with storing data for the current user, which are sometimes called CRUD functions. CRUD means Create, Read, Update, Delete:

```typescript
export interface IBackend {
    /...

  /*** Adds an item for the given user. Works with any collection, as long as you have set up firestore rules to allow
   * writes. */
  addUserItem<T>(collectionName: string, uid: string, item: T): Promise<AddResult>;
  
  /*** UPdates an item for the given user. Works with any collection, as long as you have set up firestore rules to allow
   * writes. */
  setUserItem<T>(collectionName: string, id: string, item: Partial<T>): Promise<SetResult>;
  
  /*** Deletes an item for the given user. Works with any collection, as long as you have set up firestore rules to allow
   * writes. */
  deleteUserItem(collectionName: string, id: string): Promise<DeleteResult>;
  
  /*** Gets items for the given user. Works with any collection, as long as you have set up firestore rules to allow
   * reads. */
  getUserItems<T>(collectionName: string, uid: string): Promise<GetListResult<T & WithId & WithUid>>;
}
```

Notice the `<T>` on most of these functions - this is using generics in Typescript. What this means is you can design your own type, and these functions will work with *that* type. The reason this is good is you get checks during compile time that you have only used the correct field names and types.

The `AddResult` and `SetResult` return values are another Firestarter feature, which return the result if successful, and any failure message if not. Doing this avoids having to handle Firebase exceptions in code, and let's us be sure we have handled all the error conditions.

## How to add a bot

The code to add a bot is quite simple, it is this:

```typescript
/* Add an item for the current logged in user, 
   in the collection bots, with all the fields
   entered in the form: */

await backend.addUserItem('bots', user.uid, { name, context, useFirstResponseAsMessage, initialMessage });
```

Before you start copying this... there is a bit more that is needed, like where does `user` come from? how do we get the field values, and what happens after we add a bot? Have a think about that before we continue and get all that hooked up.

### Getting form values

Getting the form values with `react-hook-form` is as simple as asking for them in the submit function:

```typescript
const onSubmit = async ({ name, context, useFirstResponseAsMessage, initialMessage }: FormData) => {
  // Code to go here that will use the form values...
};
```

The reason this works is that the `handleSubmit` function provided by `react-hook-form` deals with getting these values and passing them to `onSubmit`.

### Getting context

In Firestarter we have a helper function that will get the details of the current user, if you are logged in.

To do this we get this from the React Context set up by Firestarter, and while we are at it we can get a reference to `backend` which allows us to do the save, and `addToast` which we will use later to alert the user to the success or failure of the save.

```typescript
const { addToast, backend, user } = useContext(Context);
```

### Silent Saving

Now we have enough to do the save, at least silently without telling the user. The code is this:

```typescript
const onSubmit = async ({
  name,
  context,
  useFirstResponseAsMessage,
  initialMessage,
}: FormData) => {
  if (user) {
    await backend.addUserItem("bots", user.uid, {
      name,
      context,
      useFirstResponseAsMessage,
      initialMessage,
    });

    // .. Code to redirect to another page and show success alert
  }
};
```

To unpack this:

* We accept the form values that the `react-hook-form` library will provide us.
* We use `async` because we need to wait on the success/failure of adding the item.
* We check if there is still a user (they may have logged out since the form was loaded, for example).
* If there is a user, we then make the call to `addUserItem` to save the bot.
* There is a comment for the next thing, which is to alert the user about what just happened.

### Saving alerts

Finally we need to add code to check the result. What we want is:

* If successful, redirect back to the bot management to see your bot in the list. Tell the user it was a success.
* Otherwise tell the user it failed.

Here is the code:

```typescript
const onSubmit = async ({
  name,
  context,
  useFirstResponseAsMessage,
  initialMessage,
}: FormData) => {
  if (user) {
    const result = await backend.addUserItem("bots", user.uid, {
      name,
      context,
      useFirstResponseAsMessage,
      initialMessage,
    });

    if (result.result === 'success') {
      addToast('Your bot has been added', 'success');
      await router.push("/chatbot");
    } else {
      addToast('There was a problem adding your bot. Try again later.', 'danger');
    }
  }
};
```

This code needs an extra import:

```
import router from "next/router";
```

You can now replace your current `onSubmit` function with this. Check that you have all the required imports for all the code so far, shown below:

```typescript
import { Context } from "@/context/Context";
import router from "next/router";
import React, { useContext } from "react";
import { FieldError, useForm } from "react-hook-form";
import { Alert } from "../Alert";
```

Now try it. Visit [http://localhost:3000/chatbot/new](http://localhost:3000/chatbot/new) and fill in the top 2 fields and click "ADD BOT".

If you do, it will say "*There was a problem adding your bot. Try again later.*".

Yuk!!!! Why is that?

Check the console logs in your browser:

If it says `Missing or insufficient permissions.`, then this is expected. Sorry for the trick! We need to configure security rules to allow users to add to this new database collection called `bots`. We will do this next.

!!! note
  
    If the error says something other then "Missing or insufficient permissions.", then we have a problem! Check your internet connection, that the code is correctly pasted, and also check your Firebase configuration again in `config.ts`. If that all looks good, please reach out and I will try to help.

## Next steps

The next step in the tutorial is coming soon.
