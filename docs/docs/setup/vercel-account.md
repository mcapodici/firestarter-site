# Vercel Account

To set up your Vercel account:

* Create an account with Vercel [https://www.vercel.com/](https://www.vercel.com/)
* Select Add New -> Project
* Under "Import Git Repository" select the Github repo you created
* Under Framework Preset, select `Next.js`
* Change the root directory to `nextjs`
* Under Build and Output settings, override the following:
    * Build Command: `yarn run build`
    * Install Command: `yarn install`
* Click Deploy
* Check that the deploy runs successfully. To do so:
    * Click Project
    * Select your new Project
    * Once successful, you will see details for accessing your site like this:

![Vercel Success](/assets/vercel-success.png)

* Test that it is working. Things to check:
    * Click one of the domains
    * The site should load
    * You should be able to sign up and log in
    * Once you have signed up and logged in, you should be able to see the account in your Firebase project.


* Optional: Set up domain name
    * To link your own domain name, follow the steps here: [https://vercel.com/docs/concepts/projects/domains/add-a-domain](https://vercel.com/docs/concepts/projects/domains/add-a-domain)

