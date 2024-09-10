# 2 - Heroku Test

## I. Fork the test repository

- Head to https://github.com/tonethar/HerokuTest and **Fork** your own copy of it
  - keep the fork you made open in a web brpwser tab, or copy the URL for later
  - you don't need to clone to your desktop yet
- Look at the source code of your new repository - it is a simple web server that will echo "Hello!" to the browser
- Note the "start" script in **package.json** - this is what Heroku will run after it has downloaded all of the required packages from npm

![screenshot](![screenshot](./_images/heroku-2.png))

---

## II. Pushing/Deploying to Heroku
- Follow the instructions in the "Pushing to Heroku" DOC, which is located in the myCourses *Content* Section, *Week-3*, *Guides & Links*
  - Here, you can deploy your forked copy of “HerokuTest”

![screenshot](./_images/heroku-3.png)

- Clicking the "View" button will launch the app in a web browser
  - copy the  browser link, you'll need it later when you submit this assignment

![screenshot](./_images/heroku-4.png)

- If everything above works correctly, move on

---

## III. Clone your forked respository

- Now you need to clone your forked **HerokuTest** repository to your desktop
- If you don't already have something like this, create a folder on your PC named **430-files** or similar. Put it someplace easy to find
- Now open GitBash in that folder:
  - you might be able to right-click inside the folder to do so OR
  - you could open up a GitBash terminal window, then type `cd ` (`cd` followed by a space) and then drag drop the folder into the the terminal window, and then press enter
  - verify that your current working directory is **430-files** by typing `pwd`
- Clone your forked repository to the **430-files** folder:
  - type `git clone <clone-url-to-your-HerokuTest>`
- Verify that you have cloned the **HerokuTest** folder and files to your desktop

---

## IV. Edit HerokuTest
- Open the HerokuTest folder in VScode ("Open Folder" in VSCode OR do a drag/drop)
  
---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [1 - Git & Heroku Setup](1-git-and-heroku-setup.md)  |  [**IGME-430**](../) | ???

