# Project 1 - "Get Going!" Checkpoint

## I. Get Started
- Complete the express HW up to and including [14 - Finish up the hoot admin page](../exercises/14-finish-up-hoot-admin.md)
- Duplicate the entire **router-app-POST** folder and re-name the copy to **p1-430-&lt;abc1234>** where `abc1234` is your RIT id
- Open the folder in VSCode - them `npm i`, `npm test`, `npm run dev` to be sure that everything still works

---

## II. Create a Project 1 repo on GitHub
- Overview: You need to create a new project 1 repo on GitHub, and connect your local **p1-430-&lt;abc1234>** repo to it
- This previous exercise will be a good reminder on how to do this **-->** [9 - Putting our project on Heroku](../exercises/9-putting-project-on-heroku.md)
  - name this new remote repo **p1-430-&lt;abc1234>** and make it empty, and **@--->** ***private*** **&lt;---@** visibility
  - after you have created it, add [`tonethar` (me)](https://github.com/tonethar) as a collaborator so that I can see this repo
- Now you need to change the "origin url" of your local repo to the new project 1 repo you just created:
  - reference: https://devconnected.com/how-to-change-git-remote-origin/
  - to change the remote url, type: `git remote set-url origin https://github.com/tonethar/<your-remore-repo-name>.git`
  - to verify the change, type: `git remote -v`
  - example - what I typed for my remote was `git remote set-url origin https://github.com/tonethar/p1-430-abc1234.git`
- Type `git status` to be sure that your local repo is all up to date (if not, `git add`, `git commit` etc)
- Type `git push` to push this local repo up to github. Then check the remote github repo in your web browser to verify it's been updated

---

## III. Create a Project 1 app on Heroku

