# Tech Stack

Firestarter uses the tech stack explained on this page. Read on to learn, but don't worry, step by step installation instructions are given so you don't need to be an expert in any of these.

## Cloud Services

### Firebase

Firestarter uses Google's [Firebase](https://firebase.google.com/) platform.

Firebase is a cloud-based platform offered by Google for building and running web and mobile applications. 

It provides several services such as authentication, real-time database, cloud storage, hosting, and more. 

Authentication allows developers to add secure user authentication to their applications using email/password, phone number, or social login providers such as Google, Facebook, Twitter, and more. 

Firestore is a NoSQL document-based database service offered by Firebase that allows developers to store and sync data in real-time. 

👁️‍🗨️ Firestarter currently uses just the authentication and database features. It uses email/password authentication only.

### Vercel

[Vercel](https://vercel.com) (previously called Zeit before 2019) is the company behind NextJS and provide a very convenient and free / cheap way to host NextJS applications.

I recommend using Vercel to get started with Firestarter, but you have the option to deploy your site to another host, such as Firebase's site hosting, Digital Ocean or AWS.

### Github Actions

[Github actions](https://github.com/features/actions) are used to build, test and deploy the application when you push commits to Github. This is very convenient to make sure you have consistent build and test process for every commit, and making it easy to deploy (there is nothing to do!).

However if you don't have to use it. You could for example work locally using Git, and delpoy to both Vercel and Firebase by running command line. 

### Firebase vs. Vercel

It may be confusing as to what Firebase does and what Vercel does when hosting your application. Here is the distinction:

* Vercel will generate and host the static html files that serve the various pages on the site. It will bundle the Javascript needed to run the site.

* Firebase will store user authentication data and user data. Firebase is called by the Javascript on each page.

Note: This is the case for Firestater, but Vercel and Firebase can do much more than what is listed here.

## Platforms and Code

### Next.js and React

Firestarter uses [Next.js](https://nextjs.org/) for building out the site's components and pages and providing a slick, fast experience for the users.

Next.js is a React-based framework used for building server-side rendered web applications. It is designed to make it easy for developers to build high-performance web applications with features such as server-side rendering, automatic code splitting, and static site generation. 

Next.js offers an intuitive API for building dynamic applications while also providing robust support for static site generation, allowing developers to generate pre-rendered pages for improved performance and SEO. 

👁️‍🗨️ Firestarter only uses Next.js to generate static HTML, with the data from the server being fetched and rendered by Javascript by calling the Firebase APIs.


### Typescript

Firestarter uses [Typescript](https://www.typescriptlang.org/), which is a language that is similar to Javascript and compiles to Javascript. It adds types to the languages, so you can specify that an argument to a function is a number or a string, whereas in Javascript there is no way to specify or check this at edit time.

Firestarter uses some intermediate features of Typescript such as generics and unions. If these are not familiar, fear not, as we provide example usages so you can see the pattern of how to build against these. By using these features we can make it a bit easier to build out some functionality in your app quickly.