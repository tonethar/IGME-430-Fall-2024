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
- Quote
  - id:long
  - text:string
  - author:string
 

## Version #2 - Base Server Functionality

- Endpoints:
  - `GET quotes/` - returns all quotes
  - `GET quotes/id` - returns one quote with matching `id`
  - `GET quotes/random` - returns one random quote
  - `GET quotes/random/n` - returns `n` number of quotes

## Reference
- https://jelvix.com/blog/software-requirements-specification
- https://www.rfc-editor.org/rfc/rfc9110.html
