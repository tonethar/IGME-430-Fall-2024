# HW - Simple HTTP Server

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
- ESLint for automatic code quality checking - https://eslint.org/
  - we have a `npm test` script that runs ESLint, and gives us warnings and errors
- `fs.readFileSync()` for loading files on the server
- Endpoints that return:
  - `text/html`
  - `application/json`
  - `text/plain`
  - `image/png`
- Continuous Integration with GitHUb Actions
  - GitHub will run `npm test` on our code and tell us if it fails - look under the Actions tab in GitHub (on the repo for your Forked Simple HTTP Server starter code)
  - Look for the "Assignment Submission Guide (GitHub, GitHub Actions, Heroku)" PDF document in myCourses/Content/Guides
  
---

## III. Get started!

