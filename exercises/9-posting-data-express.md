# 9 - `POST`ing data to express

- We have seen how to pass data to an express app with `GET` via URL params and URL routes ...
- now let's see how to send data to express via `POST`

## I. Get Started
- Duplicate the entire **router-app-passing-params** folder and re-name the copy to **router-app-POST**
  - you might want to delete the **node_modules** folder before you make the copy; if so, don't forget to `npm i` below
- Open up **router-app-POST** in VSCode and `npm i`,  `npm run dev`
- Verify that the app's endpoints still work in the browser

---

## II. Setting up a local Git repository
- It's about time to get this posted to Heroku, and to do that we'll need a Git repo
- In VSCode's Terminal, type `pwd` to make sure that your current working directory is **router-app-POST**
- Type `git init` to create a new git repository
  - in the console you should see `Initialized empty Git repository in ...`
  - BTW: if you type `ls -al` you'll see a **.git**  folder now - this is where the file changes you make are tracked
  - BTW: if you type `ls .git` you'll see its contents
  - BTW: never modify any of the files in the **.git** - pretty much just ignore it
- We need to tell git which files and folders to exclude from version tracking:
  - type `touch .gitignore` to create an empty text file named **.gitignore**
  - make **.gitignore** look like this:

**.gitignore**
```
node_modules
.DS_Store
```

- BTW: If you want a more exhaustive list of files for this **.gitignore** file, you can use GitHub's "Node" version of **.gitignore**, here it is (just be sure to add **.DS_Store** to the end of it) --> https://github.com/github/gitignore/blob/main/Node.gitignore
- Now let's get our local (currently empty) repo tracking our project files, and commit them:
  - `git status`
  - 
 
---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**8 - Passing params to `express`**](8-passing-params-in-express.md)  |  [**IGME-430**](../) | ???
