# HW - Streaming Media

## I. Overview


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

- To make it more obvious when you are viewing an HTML page as opposed to solely a media file, add the following CSS to the `<style>` tag of **client2.html**

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

