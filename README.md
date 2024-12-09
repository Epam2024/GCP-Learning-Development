# GCP-Learning-Development
GCP-Learning &amp; Development

Quiz :-
##Why might a Google Cloud customer choose to use Cloud Run functions?

Their application contains event-driven code that they don't want to provision compute resources for.

##Select the managed compute platform that lets you run stateless containers through web requests or Pub/Sub events.

Cloud Run

##Which of these statements about Cloud Run functions are correct? Select three. Cloud Run functions:

Can be used to extend Cloud services.
Is integrated with Cloud Logging.
Is a scalable functions-as-a-service platform.






###########################################################################################################################################################################################################################



Git Error during this excercise and troubleshoot steps :-

1. ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/Epam2024/GCP-Learning-Development.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.


Troubleshoot Steps :-

a. git fetch origin
b. git merge origin/main


Then,the error appears as :-

The error fatal: refusing to merge unrelated histories occurs because your local branch and the remote branch have entirely separate commit histories. This usually happens when:

The remote repository already contains some commits (e.g., a README or other initial content).
Your local repository was initialized independently without fetching from the remote repository.

Troubleshoot Steps :-
a. git merge origin/main --allow-unrelated-histories
b. Open the conflicting files and resolve the differences manually. Conflict markers look like this:
plaintext
Copy code
<<<<<<< HEAD
Your local changes
=======
Remote changes
>>>>>>> origin/main
a. After resolving conflicts, stage the files:
b.  git add <file-with-conflict>
c.  git commit
d. git push origin main

##############################################################################################################################################################################################################################

You can list the active account name with this command:
gcloud auth list

You can list the project ID with this command:
gcloud config list project

From Cloud Shell, enable the Cloud Run API :
gcloud services enable run.googleapis.com

Set the compute region:
gcloud config set compute/region us-central1

Create a LOCATION environment variable:
LOCATION="us-central1"

Now, build your container image using Cloud Build by running the following command from the directory containing the Dockerfile. (Note the $GOOGLE_CLOUD_PROJECT environmental variable in the command, which contains your lab's Project ID):

gcloud builds submit --tag gcr.io/$GOOGLE_CLOUD_PROJECT/helloworld

List all the container images associated with your current project using this command:
gcloud container images list

Register gcloud as the credential helper for all Google-supported Docker registries:
gcloud auth configure-docker

To run and test the application locally from Cloud Shell, start it using this standard docker command:

docker run -d -p 8080:8080 gcr.io/$GOOGLE_CLOUD_PROJECT/helloworld

###Task 4. Deploy to Cloud Run

Deploying your containerized application to Cloud Run is done using the following command adding your Project-ID:
gcloud run deploy --image gcr.io/$GOOGLE_CLOUD_PROJECT/helloworld --allow-unauthenticated --region=$LOCATION


###Task 5. Clean up

You can either decide to delete your Google Cloud project to avoid incurring charges, which will stop billing for all the resources used within that project, or simply delete your helloworld image using this command :

gcloud container images delete gcr.io/$GOOGLE_CLOUD_PROJECT/helloworld

To delete the Cloud Run service, use this command :
gcloud run services delete helloworld --region=us-central1



