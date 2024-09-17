# 4 - Simple HTTP Server - add an Ajax client

## I. Recap - what was new in *Heroku Test* & *Simple HTTP Server HW*?
- ***Quite a bit!***

### IA. Your developer workflow:
- forking the starter code on github.com
- cloning it to a local repository - `git clone <url-to-forked-repo>`
- making changes
- committing those changes to your local repository - `git status`, `git add .`, `git commit -m "message`
- pushing those local changes to your forked remote repository on GitHub - `git push`

### 1B. Heroku:
- linking to a GitHub repository
- setting up *auto deployment*
- setting up *continuous integration*

### 1C. Code quality:
- ESLint, a `"devDependency"` for development, that Heroku won't download
- running tests with `npm test`
- Continuous integration - where GitHub Actions run our `npm test`:
  - Heroku won't accept the code if it fails the tests
  - if the code passes the tests, Heroku will accept the new code, and run `npm i` and `npm start` on it

### 1D. Development Environments/"Stages"
- *Development* - what you are doing on your local machine
- *Release* or *Production* - what you push to GitHub, and what is running on Heroku
- See relevant **#430-career** thread for more info


---

## II. In-class Exercise - add a "rich client" to *Simple HTTP*



---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**2 - Heroku Test**](2-heroku-test.md)  |  [**IGME-430**](../) | [**5 - Streaming Media HW**](5-streaming-media.md)
