# 3 - *HW - Simple HTTP Server*

- See myCourses Content/Assignments for the instructions PDF
- See myCourses dropbox for due date

---

## I. Working Example

### Heroku Links
- https://acjvks-simple-http-server-eb5e0c2bf4e7.herokuapp.com/ - default home page
- https://acjvks-simple-http-server-eb5e0c2bf4e7.herokuapp.com/page2
- https://acjvks-simple-http-server-eb5e0c2bf4e7.herokuapp.com/hello
- https://acjvks-simple-http-server-eb5e0c2bf4e7.herokuapp.com/time
- https://acjvks-simple-http-server-eb5e0c2bf4e7.herokuapp.com/helloJSON
- https://acjvks-simple-http-server-eb5e0c2bf4e7.herokuapp.com/timeJSON
- https://acjvks-simple-http-server-eb5e0c2bf4e7.herokuapp.com/fake - returns default home page
- https://acjvks-simple-http-server-eb5e0c2bf4e7.herokuapp.com/dankmemes


### `localhost` links
- http://localhost:3000 
- http://localhost:3000/page2
- http://localhost:3000/hello
- http://localhost:3000/time
- http://localhost:3000/helloJSON
- http://localhost:3000/timeJSON
- http://localhost:3000/fake
- http://localhost:3000/dankmemes

---

## II. What's new in this assignment?
- [`fs.readFileSync()`](https://nodejs.org/api/fs.html#fsreadfilesyncpath-options) for loading static files on the server
- **Endpoints** that return:
  - `text/html`
  - `application/json`
  - `text/plain`
  - `image/png`
- **ESLint** for automatic code quality checking - https://eslint.org/
  - we have a `npm test` script that runs ESLint, and gives us warnings and errors - before we run the code!
  - ESLint is a "developer dependency" that we use on our local development machine while we add features/debug, but NEVER in production. Heroko won't download any developer dependencies!
- **Continuous Integration** with **GitHub Actions**
  - GitHub will run `npm test` on our code and tell us if it fails - look under the Actions tab in GitHub (on the repo for your Forked Simple HTTP Server starter code)
  - If we check the "Wait for CI to pass before deploy" on Heroku - the new GitHub code will NOT be depolyed to the running version on Heroku!
  - Look for the ***"Assignment Submission Guide (GitHub, GitHub Actions, Heroku)"*** PDF document in myCourses/Content/Guides
  - https://en.wikipedia.org/wiki/Continuous_delivery
  - https://en.wikipedia.org/wiki/Continuous_integration
  
---

## III. Get started!
- Grab the instructions PDF (in myCourses Content/Assignments)
1) On GitHUb, ***fork*** the starter files respository - https://github.com/IGM-RichMedia-at-RIT/Simple-HTTP-Assignment-Start
   
2) Using GitBash, `cd` to your **430-files** folder (or wherever you are putting your course files)

3) Type `git clone <url-to-your-forked-repo>`

4) Open the **Simple-HTTP-Assignment-Start** folder (or whatever you named it) with VSCode

5) Open the Terminal in VSCode, and type `pwd` to verify that you are in the correct folder

6) `npm init -y`

- now you have a **package.json** file

7) Install ESLint:

- `npm i -D eslint eslint-config-airbnb eslint-plugin-import`

*OR*

- `npm install --save-dev eslint eslint-config-airbnb eslint-plugin-import`

*... they do the same thing ...*

- now you have a `"devDependencies": {...}` key in **package.json**

8) create `src` folder

- and so on

---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**2 - Heroku Test**](2-heroku-test.md)  |  [**IGME-430**](../) | ???
