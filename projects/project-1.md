# Project 1 (DRAFT)

## I. Overview
- Web APIs are ubiquitous in the modern world as a means of accessing and interacting with a dataset. Oftentimes companies provide APIs to provide limited or complete access to the data they have and manage. Many of these APIs are publicly available such as the Google Maps API, Spotify API, PokeAPI, and many others. They allow other developers to build rich web applications and experiences that are augmented by the data they get. Private Web APIs are also used by nearly every company to pass data between various internal systems and tools.
- *For this project, you will not be utilizing one of these preexisting APIs. Instead, you will take a JSON dataset and create a Web API that allows others to access, search, filter, and edit your dataset.*

---

## II. Files
- [Project 1 Requirements (PDF)](_files/430%20Project%201%20(New%2C%202024).pdf)
- [430 Project 1 Datasets.zip (ZIP)](_files/430%20Project%201%20Datasets.zip) 

---

## III. Additional Requirements
- We will be utilizing the [express](https://www.npmjs.com/package/express) libary (in lieu of node's built-in [http](https://nodejs.org/api/http.html))
- You will add a `/random` endpoint to your API
- You will add a `/recent` endpoint to your API

---

## IV. Example
- https://willoughby-project-1-5f0f90052f40.herokuapp.com/

---

## V. `GET` endpoints

### V-A. Array of ALL elements - `/api/countries`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/countries

### V-B. One random element - `/api/country/random`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/random

### V-C. Most recently added element - `/api/country/recent`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/recent

### V-D. `/api/country/:name`
- http://localhost:3000/api/country/alBani


