---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "mdl-api-key: [client_id]"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`mdl-api-key: [client_id]`
`Authorization: Bearer [access_token]`

<aside class="notice">
You must replace <code>[client_id]</code> with your personal API key.
</aside>

# Titles

## Get a title

```shell
curl "https://api.mydramalist.com/titles/24640" \
  -H "Content-Type: application/json" \
  -H "mdl-api-key: [client_id]"
```

> The above command returns JSON structured like this:

```json
{
  "id": 24640,
  "slug": "24640-test-content",
  "title": "Test Content",
  "original_title": "Test Content Native 2",
  "year": 2018,
  "rating": 0,
  "permalink": "https://mydramalist.com/24640-test-content",
  "synopsis": "Aenean ligula eget dolor. Vestibulum turpis sem, aliquet eget, lobortis pellentesque, rutrum eu, nisl. Sed cursus turpis vitae tortor. Praesent ac sem eget est egestas volutpat. Donec sodales sagittis magna.\n\nQuisque libero metus, condimentum nec, tempor a, commodox mollis, magna. Quisque ut nisi. Aliquam erat volutpat. Etiam feugiat lorem non metus. Etiam rhoncaus.\n\nDonec interdum, metus et hendrerit aliquet, dolor diam sagittis ligula, eget egestas libero turpis vel mi. Nunc interdum lacus sit amet orci. Suspendisse potenti. Proin sapien ipsum, porta a, auctor quis, euismod ut, mi. Cras dapibus. test24 test2",
  "type": "Movie",
  "language": "Japanese",
  "images": {
    "thumb": "https://i.mydramalist.com/q2ERKt.jpg",
    "medium": "https://i.mydramalist.com/q2ERKm.jpg",
    "poster": "https://i.mydramalist.com/q2ERKc.jpg"
  },
  "alt_titles": [
    "Test content"
  ],
  "country": "Japan",
  "episodes": 1,
  "watchers": 4,
  "released": "2018-01-02",
  "genres": [
    "action",
    "adventure",
    "business"
  ],
  "tags": [
    "Food",
    "manga",
    "time travel",
    "Adapted From A Novel",
    "instant attraction",
    "anime",
    "Mystery",
    "Nice Male Lead"
  ],
  "trailer": 0,
  "runtime": 30,
  "certification": "Not Yet Rated",
  "status": "",
  "updated_at": 1501468950
}
```

This endpoint retrieves a specific title.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://api.mydramalist.com/titles/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The identifier of the title to be retrieved.

## Get title ratings
## Get all credits
## Get all reviews
## Get related titles

#People

##Get a single person
##Get title credits

#Reviews

##Create a review
##Update a review
##Delete a review

#Sync
##Get last activities
##Get watchlist
##Add to watchlist
##Remove from watchlist
