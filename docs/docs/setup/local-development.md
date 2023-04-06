# Local Development

## Install Node.js

You need Node.js installed. We recommend using version 18 to match what we are using in Github actions. However any version 12 or higher should work.

You can download Node from [https://nodejs.org/en](https://nodejs.org/en).

## Install Yarn

Firestarter use Yarn to install Node packages and run scripts.

To install Yarn, run this from the command line:

```
npm install --global yarn
```

## Test that your local environment is working

Change directory to the root of the repo you have cloned, then run these commands to build the project:

```
cd nextjs
yarn build
```

Make sure that no errors are reported. It should have some build output, followed by `Done in XX.XXs` at the end.

Now run the tests:

```
yarn test --watchAll
```

After about 40 seconds or so, it should say all the tests have passed, i.e. you don't see any red or the word fail, but something like this:

```
Test Suites: 14 passed, 14 total
Tests:       90 passed, 90 total
Snapshots:   0 total
Time:        44.568 s, estimated 59 s
Ran all test suites.
```

## Running it locally

Run the following command 

```
yarn dev
```

Open your browser to [http://localhost:3000](http://localhost:3000)

You should now see the demo site, and be able to sign up and log in. It will currently use the demo firebase account that I own. You will change the settings to use your own one later in the setup steps.

[Firebase Account >>>](firebase-account.md){ .md-button }