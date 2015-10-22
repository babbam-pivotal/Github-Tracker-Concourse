# Github-Tracker-Concourse

##Objective:

Aim of this integration is to streamline the following flow - 

1. Commit the changes to my story
2. Push to GitHub
3. Click Finish on story in tracker
4. Wait for green build
5. Wait for green test
5. Deploy to staging
6. Click Deliver in Tracker

##Configuration:

Step 1 - Create a pseduo user whose sole purpose is to pass commits to Tracker stories. Make sure the this user is a member of ALL projcts you wish to push commits to.
Step 2 - Copy the API token for the pseudo user from profile page.

![apitoken](https://cloud.githubusercontent.com/assets/11538159/10656280/ece9033a-78c8-11e5-94c0-a36383441cd5.png)

Step 3 - Access the GitHub repository that yo uplan to associate with Tracker. Go to Settings > Webhooks & Services > Add Services > PivotalTracker.
Step 4 - Enter the Tracker API token copied in Step 2. Rest of the settings can be left blank for this test. Default setting includes all branches.

Once the above configuration is done, you're ready to start committing!

##Test:

Make changes to files in the repository used above and tag the Tracker story in the comment section - [(Finishes|Fixes|Delivers) #TRACKER_STORY_ID]

When you push to GitHub, the post-receive hook will then call back to Tracker and put a comment on the story with a link to the commit on GitHub. Example: [Fixes #1092834]

<img width="324" alt="commitmsg" src="https://cloud.githubusercontent.com/assets/11538159/10656230/7e640a4a-78c8-11e5-8967-b33e167ebbe0.png">

At this point, we’ve eliminated step 3 from above. Now our workflow looks like this:

1. Commit the changes to my story
2. Push to GitHub
3. Wait for green build
4. Click Deliver in Tracker

##GitHub Concourse Integration:

TBD

So, here's what our development workflow now looks like - 

1. Commit the changes to my story
2. Push to GitHub

##Conclusion:

GitHub will mark stories as finished, and add a comment. CI will then run. If there’s a green build+test, it will deploy code to PCF. The deploy script 'code-deployed.rb' will then run the deliver_stories script shown above, and all stories that have been deployed will be marked as delivered.

