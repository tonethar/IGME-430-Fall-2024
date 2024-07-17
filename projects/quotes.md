# Quotes App

## Version #1 - Base Client App

### Functional Requirements for End User
  - View quote of the day
  - View new quote
  - Favorite a quote
  - Unfavorite a quote
  - View favorite quotes
  - State preservation:
    - last viewed quotes
    - all favorited quotes

### Software Requirements
- Vanillajs Implemewntation
- Vue.js Implementation

### Data Model
- All quote data is local to client
- Quote
  - id:long
  - text:string
  - author:string
 
---

## Version #2 - Base Server 

### Functionality
- Read only
- Authentication is not required
- Endpoints:
  - `GET quotes/` - returns all quotes
  - `GET quotes/id` - returns one quote with matching `id`
    - when a match can not be made, returns 404 and error info in JSON format
  - `GET quotes/random` - returns one random quote
  - `GET quotes/random/n` - returns `n` number of quotes

### Data Model
- Quote
  - id:long
  - text:string
  - author:string
 

## Reference
- https://jelvix.com/blog/software-requirements-specification
- https://www.rfc-editor.org/rfc/rfc9110.html
