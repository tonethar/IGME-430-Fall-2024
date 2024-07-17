# Quotes App

## Version #1 - Base Client App

### Functional Requirements for End User
  - View quote of the day
  - View new random quote
  - Favorite a quote
  - Unfavorite a quote
  - View favorite quotes
  - State preservation:
    - last viewed quotes
    - all favorited quotes

### Data Model
- All quote data is local to client
- Quote
  - id:integer
  - text:string
  - author:string
 
---

## Version #2 - Base Server 
- Quote data moved from client to cloud
  
### Server Functionality
- Read only
- Authentication is not required
- Endpoints:
  - `GET quotes/` - returns all quotes
  - `GET quotes/today` - returns same quote for the entire day
  - `GET quotes/id` - returns one quote with matching `id`
    - when a match can not be made, returns 404 and error info in JSON format
  - `GET quotes/random` - returns one random quote
  - `GET quotes/random/n` - returns `n` number of quotes

### Data Model
- Quote
  - id:long
  - text:string
  - author:string


---

## Version #3 - Improved App
- This version adds timestamps and tagging features

### Client
- Improved features:
  - Reorder favorite quotes list
  - Filter favorite quotes by category (tags)
  - Favorites are still stored locally
- New features:
  - Share quote
  - Filter quote search by category (tags)
    - example: "inspirational", "religious"
  - Filter quotes by creation date
    - example: View recently created

### Server
- Read only
- Authentication is not required
- Endpoints:
  - `GET quotes/random/?tags=` - returns one random quote of specified categories
    - ex. `quotes/random/?tags=funny`
    - ex. `quotes/random/?tags=funny,serious`
  - `GET quotes/random/n/?tags=` - returns `n` number of quotes of specified categories
  - `GET quotes/latest`
  - `GET quotes/latest/n`
  - `GET quotes/latest/n/?tags=`

---

## Version #4 - Final App

### Client
- App now has form for submitting suggestions for new quotes
- This version adds cloud features:
  - user accounts
    - user login & password required
    - favorites list now in cloud and visible on multiple machines
  - admin accounts (superuser)
    - CRUD operations for quotes
   
### Server
- Is now Read/Write
- Endpoints:
  - `POST `
  - ...

--- 

## Other features
- Quotes created by generative AI

---

## Reference
- https://jelvix.com/blog/software-requirements-specification
- https://www.rfc-editor.org/rfc/rfc9110.html
- https://quotemarks.app/
