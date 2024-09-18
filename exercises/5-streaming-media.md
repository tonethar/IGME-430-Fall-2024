# 5 - Streaming Media HW

- See myCourses Content/Assignments for the instructions PDF
- See myCourses dropbox for due date

---

## I. Overview
Below are the key lessons taught by this exercise.

### New Stuff
- **Serving new media types** for (`Content-Type: `) - `audio/mpeg` and `video/mp4`
- **Streaming media (audio and video):**
  - browsers no longer have to download an entire audio or video file before beginning to play it, and can instead request just part of a file - a "range" to download and play
  - HTTP response headers --> `Content-Range: ` and `Accept-Ranges: ` 
  - HTTP server status code --> `206 Partial Content`
  - HTTP request header --> `Range: ` (the browser does this for us with the `<audio>` and `<video>`) tags
- **A typical HTML "page" consists multiple "parts":**
  - an HTML file that contains marked up text, but also has a bunch of links to other resources such as external CSS style sheets, images, JS files, other media files and so on
  - as the browser is parsing and rendering the HTML file, it will make additional requests to the server for these files, ONE request per file
  - as the files arrive, the browser will gradually "assemble" the HTML page and display it to the user
  - which means: in order to display the "party.mp4" to a user, we need to implement server endpoints for both the HTML page that contains the `<video>` tag AND the "party.mp4" itself

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
1) On GitHub, ***fork*** the starter files respository - https://github.com/IGM-RichMedia-at-RIT/streaming-media-assignment
   
2) Using GitBash, `cd` to your **430-files** folder (or wherever you are putting your course files)

3) Type `git clone <url-to-your-forked-repo>`

4) Open the **streaming-media-assignment** folder (or whatever you named it) with VSCode

5) Open the Terminal in VSCode, and type `pwd` to verify that you are in the correct folder

6) `npm init -y`

    - now you have a **package.json** file

7) Install ESLint:

    - `npm i -D eslint eslint-config-airbnb eslint-plugin-import`

8) Create a `src` folder

9) And so on ...

---

## IV. Finish it up - submission instructions are in the PDF

---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**4 - Simple HTTP Server HW - add an Ajax client**](4-simple-http-add-client.md)  |  [**IGME-430**](../) | TBA
