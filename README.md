# Github-Tracker-Concourse

Objective:

Aim of this integration is to streamline the following flow - 

1. Commit the changes to my story
2. Push to GitHub
3. Click Finish on story in tracker
4. Wait for green build
5. Wait for green test
5. Deploy to staging
6. Click Deliver in Tracker

into

1. Commit the changes to my story
2. Push to GitHub

Configuration:

Step 1 - Create a pseduo user whose sole purpose is to pass commits to Tracker stories. Make sure the this user is a member of ALL projcts you wish to push commits to.
Step 2 - Copy the API token for the pseudo user from profile page.
Step 3 - Access the GitHub repository that yo uplan to associate with Tracker. Go to Settings > Webhooks & Services > Add Services > PivotalTracker.
Step 4 - Enter the Tracker API token copied in Step 2. Rest of the settings can be left blank for this test. Default setting includes all branches.

Once the above configuration is done, you're ready to start committing!

Test:


jljlfda
