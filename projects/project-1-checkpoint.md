# Project 1 - "Get Going!" Checkpoint

## I. Get Started
- Complete the express HW up to and including [14 - Finish up the hoot admin page](../exercises/14-finish-up-hoot-admin.md)
- Duplicate the entire **router-app-POST** folder and re-name the copy to **p1-430-&lt;abc1234>** where `<abc1234>` is your RIT id
- Open the folder in VSCode - them `npm i`, `npm test`, `npm run dev` to be sure that everything still works

---

## II. Create a Project 1 repo on GitHub
- Overview: You need to create a new project 1 repo on GitHub, and connect your local **p1-430-&lt;abc1234>** repo to it
- This previous exercise will be a good reminder on how to do this **-->** [9 - Putting our project on Heroku](../exercises/9-putting-project-on-heroku.md)
  - name this new remote repo **p1-430-&lt;abc1234>** and make it empty, and **@--->** ***private*** **&lt;---@** visibility
  - after you have created it, add [`tonethar` (me)](https://github.com/tonethar) as a collaborator so that I can see this repo
- Now you need to change the "origin url" of your local repo to the new project 1 repo you just created:
  - reference: https://devconnected.com/how-to-change-git-remote-origin/
  - to change the remote url, type: `git remote set-url origin https://github.com/tonethar/<your-remote-repo-name>.git`
  - to verify the change, type: `git remote -v`
  - example - what I typed for my remote was `git remote set-url origin https://github.com/tonethar/p1-430-abc1234.git`
- Type `git status` to be sure that your local repo is all up to date (if not, `git add`, `git commit` etc)
- Type `git push` to push this local repo up to github. Then check the remote github repo in your web browser to verify it's been updated

---

## III. Create a Project 1 app on Heroku
- Once again, this previous exercise will be a good reminder on how to do this **-->** [9 - Putting our project on Heroku](../exercises/9-putting-project-on-heroku.md)
  - name the app **p1-430-&lt;abc1234>** where `<abc1234>` is your RIT id
  - link it your new project 1 GitHub repo
  - make sure that autodeploy and CI are enabled
  - test the Heroku project, in particular the **admin.html** functionality, and verify that it works as expected
  - make sure that the Actions tab on GitHub shows a successful run, and that the main repo page has that ***beautiful green checkmark***
- Submission, do this right now:
  - In Slack, DM to the prof the following:
    - the Project-1 GitHUb repo link (recall that this is private, and that the prof is a collaborator)
    - the Heroku link to the working app (NOT the dashboard link)

---

## IV. Choose a data source

- Choose ONE ["Data Set"](project-1.md#ii-files) file as the primary data for your app **OR**
- If you would like to utilize a dataset that covers something other than the provided datasets you are welcome to do so. However, there are a few things you must confirm before you can use it:
    1. Thedatamustbeinproper.jsonformat
    2. Thedatasetmusthavesomeamountofdatanesting.Thatmeanstheremustbe an object or array nested inside of the individual data objects.
    3. Youmustunderstandhowthatdataisorganizedandbeabletoproperlyparseit with JavaScript.
    4. Once you have confirmed the above 3 things, send the dataset to the Prof for final approval

