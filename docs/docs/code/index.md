# Firestarter Code

This is a quick introduction to the codebase, so you can understand and extend it.

## Tech Stack

Firestarter uses Next.js, React, Typescript, Firebase, Vercel and Github Actions. If you are not familiar with all of these, check out the [technologies page](../technologies.md) for a quick briefing on those and then come back.

## How Next.js is used

Next.js is a framework that allows you to use React components on the frontend and backend. It support 3 main ways to "render" something in the browser:

* SSR - Server Side Rendering. This is like the traditional web server model, where you send HTML from the server to the client. With NextJS you use React code to do this, and it is the very same code you run on the front end, allowing seamless code reuse.

* SSG - Static Generation. This is a bit like Gatsby and similar tools that create static HTML files on the server. This can be done when a page doesn't change for different users, and the content only depends on the URL.

* Frontend. Using React, we can run code in the browser and further enhance the experience on the front end.

Firestarter uses SSG and Frontend only at the moment, with almost all of the work being done in the front end.

This model allows for rapid development of features, and is ideal for working with Firebase, which is heavily biased towards this way of working. The advantage is that the browser is talking directly to the Firebase database, and pages load very quickly.

The downside is that there will be some time betweent the page loading initially and the data being loaded on to the page. We mitigate this by using "placeholder" styling to indicate which parts of the page are loading.

## Authentication

Firebase has a good authentication system, and supports many types of provider. At the moment Firestarter only uses username/password authentication.

One caveat of Firebase (which I don't like, but hey!) is you can create an account before you confirm your email address. The problem with this is that it would allow someone to 'squat' accounts that could be owned by others.

To work around this problem I have done two things. I have set the security rules to not allow activity on an account that hasn't had it's email confirmed. You will see this in the `firestore.rules` as lines like this:

```
allow read: if request.auth != null && request.auth.token.email_verified && request.auth.uid == userId;
```

In additon the user interface will prompt you to verify your email when you log in if you haven't done so already.

## Backend Facade

To make the code more friendly to unit testing, and also to simplify the React components there is an interface called `IBackend` which you will find in `IBackend.ts`.

This contains all of the authentication actions needed, and in addition some universal CRUD (create, read, update and delete) actions for data stored against the current user.

What this means is you can easily add code to store various kinds of data against the current user, without writing any additional Firebase code, or extending the `IBackend` interface.

You can see an example of the usage of this in the Todo's `index.tsx` file:

```typescript
const addTodoResult = await backend.addUserItem<Todo>(TodoCollectionName, user.uid, { title, done: false });
```

## Testing

For testing we use the [Testing Library](https://testing-library.com/) and [Jest](https://jestjs.io/). Testing Library allows us to test the user interface without the overhead (and unreliability) of using a real browser. Instead it emulates each page in memory, and then we check actions such as filling in fields and clicking buttons and assert that the correct things happen.

Testing with Firebase is a bit tricky, since there are no up to date mocking libraries for Firebase at the moment. So there is a lot of mocking parts of the Firebase API. This got a bit too much in places so there is some lack of coverage of the CRUD parts, but I hope to bridge that gap in the future.

As mention in the Setup steps, to run the tests you can run `yarn test` from the `nextjs` folder.

## Rules

As touched on earlier we have a `firestore.rules` file to define the security rules that apply to the database. The Github actions will apply changes to this made on the `main` branch. 

## Test environment (or Lack of!)

There is no support yet for a test environment within Firebase. In other words a second database for trying things out before you push changes on `main`. 

This wont be a problem most of the time, but it could come in useful to have this if you want to make changes to Firebase rules, add Firebase functions (or change them), etc. 

This is something I am thinking about and will add in the future.

## Tailwind

My approach to using Tailwind is to splatter tailwind classes everywhere, and then when I see repetition tidy up common things into the `global.css`. Your prefered approach might be different! So feel free to structure the css as you please. I started off using [Tailwind Elememts](https://tailwind-elements.com/), and some of the styles were originally from there and adapted. However I dropped use of it's NPM pacakage because it is not as React-friendly as I would like, so I reimplemented some of the affordances in React, such as the hamburger menu for narrow devices.

## React Component Archiecture

The React architecture used is very simple.

* Each page will typically use the `<Layout>` component to ensure there is the navigation bar, etc.
* The `_app.tsx` component, which is a staple of Next.js projects, sets up a React Context which allows individual pages to add alerts, check for authentication status, and access the `backend` object, which is the runtime (as opposed to testing) implementation of `IBackend`.
* For forms I tend to use `react-hook-form` library. You don't have to, but it is a very nice convenience.

## Tutorials

There is a tutorial section, and I will add a tutorial in future about how to add another page, add 



