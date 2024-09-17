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

1) Get a fresh copy of Simple HTTP Server HW
- `cd` to you local 430 working directory
- `git clone <url-to-forked-repository>`


2) Make sure everything works

- `cd` into folder
- `npm i`
- `npm test`
- `npm start`
- Check the endpoints in the browser - esp. http://localhost:3000/helloJSON and http://localhost:3000/timeJSON


3) Here's the HTML/JS for your "Rich Client":

- put this in your **client/** folder

**client/rich-client.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Rich Client!</title>

</head>
<body>

<h1>"Rich" Client for <i>Simple HTTP Server</i></h1>
<h2>View the "Hello" Message</h2>
<p><button id="btn-hello">See contents of <kbd>/helloJSON</kbd></button></p>
<div id="output-hello">???</div>

<hr>

<h2>View the "Current Time" Message</h2>

<p>You do!</p>
  
</body>
<script>
const getJsonFetch = async (url, callback) => {
  let json;
  try{
    const response = await fetch(url,{
      method: "GET",
      headers: {
        "Accept": "application/json"
      }
    });
    json = await response.json();
  }
  catch(error){
    console.log("ERROR:", error);
    json = {author: `Can't parse data file '${url}'`};
  }
  callback(json);
};

const btnHello = document.querySelector("#btn-hello");
const outputHello = document.querySelector("#output-hello");

const helloJSONURL = "http://localhost:3000/helloJSON";
const helloCallback = json => {
  outputHello.textContent = json.message || "No <kbd>.message</kbd> value found!";
};

btnHello.onclick = () => getJsonFetch(helloJSONURL, helloCallback);

</script>
</html>
```

4) Test the Rich Client by launching **rich-client.html** with LiveServer
- When you click the button, this code fails!
- If you check the console you should see a CORS error - because LiveServer is running on port 3000, and our server is running on port 5500.
- Stop LiveServer
- There are a number of ways to fix this - but the most appropriate way in this instance is to have our node code "serve up" **rich-client.html** - you DO this:
  - Write and export a `getRichClient` function in **htmlResponses.js**
  - Create a `/rich-client` endpoint in **server.js**
  - Quit and restart node.js so that the changes take
  - Head to http://localhost:3000/rich-client to verify your new endpoint works
  - Test the Rich Client by clicking the button  - it should function now! BECAUSE NOW the rich-client "front end" is running on the same port as the web service (meaning `/helloJSON`) "back end"

---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**2 - Heroku Test**](2-heroku-test.md)  |  [**IGME-430**](../) | [**5 - Streaming Media HW**](5-streaming-media.md)
