# HW - Streaming Media

- See myCourses Content/Assignments for the instructions PDF
- See myCourses dropbox for due date

---

## I. Overview
The key lessons taught by this exercise:
### A. Reinforcing things you have seen before:
  - **Your developer workflow:**
    - forking the starter code on github.com
    - cloning it to a local repository - `git clone <url-to-forked-repo>`
    - making changes
    - committing those changes to your local repository - `git status`, `git add .`, `git commit -m "message`
    - pushing those local changes to your forked remote repository on GitHub - `git push`
  - **Heroku:**
     - linking to a GitHub repository
     - setting up *auto deployment*
     - setting up *continuous integration*
  - **Code quality:**
    - ESLint, a `"devDependency"` for development, that Heroku won't download
    - running tests with `npm test`
    - Continuous integration - where GitHub Actions run our `npm test`:
      - Heroku won't accept the code if it fails the tests
      - if the code passes the tests, Heroku will accept the new code, and run `npm i` and `npm start` on it
  - **Development Environments/"Stages"**
    - *Development* - what you are doing on your local machine
    - *Release* or *Production* - what you push to GitHub, and what is running on Heroku
    - See relevant **#430-career** thread for more info

### B. New Stuff

---

## II. Test Links

### Heroku

- https://acjvks-streaming-media-28b1ee1e434d.herokuapp.com/
- https://acjvks-streaming-media-28b1ee1e434d.herokuapp.com/party.mp4
- https://acjvks-streaming-media-28b1ee1e434d.herokuapp.com/page2
- https://acjvks-streaming-media-28b1ee1e434d.herokuapp.com/bling.mp3
- https://acjvks-streaming-media-28b1ee1e434d.herokuapp.com/page3
- https://acjvks-streaming-media-28b1ee1e434d.herokuapp.com/bird.mp4
- https://acjvks-streaming-media-28b1ee1e434d.herokuapp.com/beh!

### `localhost:3000`

- http://localhost:3000/ - default HTML page, and has a `<video>` tag that points at the **party.mp4** video file
- http://localhost:3000/party.mp4 - video file
- http://localhost:3000/page2 - HTML page that has an `<audio>` tag that points at the **bling.mp3** audio file
- http://localhost:3000/bling.mp3 - audio file
- http://localhost:3000/page3 - HTML page that has a `<video>` tag that points at the **bird.mp4** video file
- http://localhost:3000/bird.mp4 - video file
- http://localhost:3000/beh! - any URL other than the 6 above shows **client.html**

### Modify your HTML, a little

- To make it more obvious when you are in the browser viewing a media file embedded in an HTML page, as opposed to solely the media file, add the following CSS to the `<style>` tag of **client2.html**

```css
audio{
  border: 10px solid green;
}
```
- And add the following CSS to **client.html** & **client3.html** (this second file you will create later)

```css
video{
  width: 85%;
  border: 10px solid red;
}
```

---

## III. Get started!
- Grab the instructions PDF (in myCourses Content/Assignments)
1) On GitHUb, ***fork*** the starter files respository - https://github.com/IGM-RichMedia-at-RIT/streaming-media-assignment
   
2) Using GitBash, `cd` to your **430-files** folder (or wherever you are putting your course files)

3) Type `git clone <url-to-your-forked-repo>`

4) Open the **streaming-media-assignment** folder (or whatever you named it) with VSCode

5) Open the Terminal in VSCode, and type `pwd` to verify that you are in the correct folder

6) `npm init -y`

- now you have a **package.json** file

7) Install ESLint:

- `npm i -D eslint eslint-config-airbnb eslint-plugin-import`

8) Create a `src` folder

9) An so on ...
