# Github Actions

The Github actions in Firestarter will

* Run unit tests on every commit
* Deploy changes to Firebase rules on every commit to `main`

To get this to work, some configuration is required:

## Obtain values from Firbease account

* Log into your Firbease account, and go to the console.
* Click your project.
* Under **Get started by adding Firebase to your app**, click the Web icon that looks like `</>`.
* Copy the Project ID into a temporary file (to use later)
* Click Service Accounts, then click Generate a new private key, then click Generate key
* Open the downloaded file, and check there is a JSON file in there.
* Careful: this file contains full access to your Firebase project! Don't share this. This will be deleted once the steps are done.
  
## Add these to your actions environment

* Open your repo in Github
* Click Settings, and then click Environments
* Click Add Secret
    * For Name enter `GCP_SA_KEY`
    * For Secret enter the contents of the downloaded JSON file.
    * Click Add Secret
    * Delete the JSON file.
* Click Add Variable
    * For Name enter `PROJECT_ID`
    * For Value enter the project ID obtained earlier.
    * Click Add Variable
* Delete the temporary file.

Push an empty commit on your repsitory, you should, after a few minutes now get a green circle showing that everything is successful.

[Congratulations >>>](congratulations.md){ .md-button }