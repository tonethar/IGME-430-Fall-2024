# Project 1 - "Get Going!" Checkpoint

- *For this project, you will take a JSON dataset and create a Web API that allows others to access, search, filter, and edit your dataset.*

---

## I. Get Started
- Complete the express HW up to and including [15 - Notes & Errata](../exercises/15-notes-and-errata.md)
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
  - to change the remote url of the repo, type: `git remote set-url origin https://github.com/tonethar/<your-remote-repo-name>.git`
  - to verify the change, type: `git remote -v`
  - example - what I typed for my remote was `git remote set-url origin https://github.com/tonethar/p1-430-abc1234.git`
- Type `git status` to be sure that your local repo is all up to date (if not, `git add`, `git commit` etc)
- Type `git push` to push this local repo up to github. Then check the remote github repo in your web browser to verify it has been updated

---

## III. Create a Project 1 app on Heroku
- Once again, this previous exercise will be a good reminder on how to do this **-->** [9 - Putting our project on Heroku](../exercises/9-putting-project-on-heroku.md)
  - name the app **p1-430-&lt;abc1234>** where `<abc1234>` is your RIT id
  - link it your new project 1 GitHub repo
  - make sure that autodeploy and CI are enabled
  - test the Heroku project, in particular the **admin.html** functionality, and verify that it works as expected
  - make sure that the Actions tab on GitHub shows a successful run, and that the main repo page has that ***beautiful green checkmark***

---

## IV. Choose a data source

- Choose ONE ["Data Set"](project-1.md#ii-files) file as the primary data for your app **OR**
- If you prefer to utilize a dataset that covers something other than the provided datasets you are welcome to do so. However, there are a few things you must confirm before you can use it:
    1. The data must be in the JSON format, in a **.json** file
    2. The dataset must have some amount of data nesting. That means there must be an object or array nested inside of the individual data objects
    3. You must understand how that data is organized and be able to properly parse it with JavaScript
    4. Be sure that there is a unique identifier for each element of data - for example:
       - each pokemon has a unique `.id`
       - each country has a unique `.name` (but maybe you want to assign each a GUID or a country code?)
       - each book has a unique `.title` (but maybe you want to assign each a GUID or an ISBN?)
    5. Once you have confirmed the above 3 things, send the dataset to the Prof for final approval

---

## V. Create an  `/"all items"` endpoint
- This will return your entire dataset:
  - this endpoint will be helpful in the debugging process as we build out our server endpoints
  - in the "real world" we would very likely NOT do this - but here our dataset is small so it's OK
- For your project, replace `/"all items"` with a meaningful name, depending on your dataset, examples:
  - `/books` or `/all-books` for the books dataset
  - `/countries` or `/all-countries` for the countries dataset
  - `/pokemon` or `all-pokemon` for the pokemon dataset
- For your API, you must use the same patterns that we did with the `/quotes` endpoint, meaning:
  - 1. there must be a **p1-db.js** that loads the **.json** file
    - **p1-db.js** has ***public methods*** for accessing and searching the data, for example:
      - `getAllBooks()` - returns an array of all the books
      - `getRandomBook()` - returns a single random book
      - `getRecentBook()` - returns the most recently added book (the last one in the array)

---

### V-A. Hints
- Note: for this example, I am going to assume that the *countries* dataset was chosen

---

1. Put your chosen dataset file in the **src/data** folder

---

2. Duplicate **db.js** and name it **p1-db.js**

---

3. In **p1-db.js**:
    - A. modify the code so that your dataset file is loaded (instead of **quotes-data.json**)
    - B. rename `getAllQuotes()` to `getAllXXX()` where `XXX` is the name of the elements of your dataset - ex. `getAllCountries()` - and modify the code to return all of the elements of your dataset in an array.
      - ***IMPORTANT*** Be sure to send back a *copy* of the original data (and NOT a reference to the original data) for this and all future DB endpoints.
      - example - this is how I implemented `getAllCountries()` - `const getAllCountries = () => [...countries]; // made a copy with array destructuring`
    - C. similarly, rename and reimplement `randomQuote()` and `recentQuote()` to return an element from your dataset

---

4. Now get rid of the "hoots" routes in **src/routes/api.js**

- **First**, *comment out* (do not delete) ALL of the code in **api.js** except for:
 
```js
const express = require('express');
const router = express.Router();
const generateNewId = () => crypto.randomUUID();

module.exports = router;
```
   
- **Second** - Test these links - the routes no longer function - but the code doesn't crash:
  - http://localhost:3000/api/hoots - returns the 404 page
  - http://localhost:3000/api/hoots/random - returns the 404 page
  - http://localhost:3000/api/hoots/recent - returns the 404 page
  - http://localhost:3000/admin - page loads, but none of the buttons work. Check browser console to see errors

---

5.  Now modify **src/routes/api.js** to use **p1-db.js** to implement:
  -  `/"all items"`
  -  `/"item"/random`
  -  `/"item"/recent`
  -  here's my version of **api.js** right now ...
 
```js
const express = require('express');

const router = express.Router();

// const generateNewId = () => crypto.randomUUID(); // NOT using yet

const db = require('../p1-db.js');

router.get('/countries', (req, res) => {
  res.json(db.getAllCountries());
});

// for you TODO: '/country/random'

// for you TODO: '/country/recent'

module.exports = router;
```
      
---

6. Test it
- Try out all 3 of these new `GET` routes locally - don't forget they will all be under http://localhost:3000/api/...`
- Push changes to GitHub and test on Heroku - here are my working links for the country dataset:
  - https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/countries
  - https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/random
  - https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/recent

---

## VI. Submission
- Be sure that the app runs on Heroku, and that GitHub Actions show that the latest push has passed the tests, and also that the main repo page has the green checkmark
- In the comments field of the myCourses dropbox, put:
  - the Project-1 GitHub repo link (recall that this is private, and that the prof is a collaborator)
  - the Heroku links to **ALL THREE*** of the working endpoints you created for your dataset
- ZIP up the project folder and upload it to myCourses
  - don't forget to first delete your **node_modules** folder


<!---
- BTW - other methods **p1-db.js** will need in the near future (examples):
        - `searchByTitle(substring)` - returns an array of books that match `substring`
        - `searchByTitleExact(title)` - returns the single exact title match, or some kind of "not found" response
          - Note: this assumes that titles are unique in the book dataset, which is not true in the "real world")
        - `searchByYearExact(year)` - returns an array of books that were published that `year`
        - `randomBook()` - returns a random book
        - `recentBook()` - returns most recently added book
        - `getPokemon(id)` - returns the single matching Pokemon or a "not found" response
          - this works for the Pokemon dataset because each individual Pokemon entry has a unique `id`
---!>
