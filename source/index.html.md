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

Welcome to the MyDramaList API! You can use our API to access MyDramaList API endpoints, which can get information on titles, people and watchlist in our database.

##Pagination

Parameter | Type    | Default | Value
--------- | ------- | ------- | -----
page      | integer | 1       | Number of page of results to be returned.
limit     | integer | 10      | A limit on the number of items to be returned, between 1 and 100.

Header  | Value
------- | ------
X-Pagination-Count | Current count of items.
X-Pagination-Limit | Items per page.
X-Pagination-Page  | Current page.
X-Pagination-Total | Total number of items.

##Required Headers
##Versioning

Any future changes to the API will be versioned in order to maintain backwards compatibility with existing integrations.

# Authentication

> To authorize, use this code:


```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "mdl-api-key: [client_id]"
```

> Make sure to replace `meowmeowmeow` with your API key.

MyDramaList uses API keys to allow access to the API. You can register a new MyDramaList API key at our [developer portal](http://example.com/developers).

MyDramaList expects for the API key to be included in all API requests to the server in a header that looks like the following:

`mdl-api-key: [client_id]`

`Authorization: Bearer [access_token]`

The bearer authorization header is scoped to an authorized platform user or application.

<aside class="notice">
You must replace <code>[client_id]</code> with your personal API key.
</aside>

# Titles

## Title Object

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
  "synopsis": "Aenean ligula eget dolor. Vestibulum turpis sem...",
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

##Person Object
##Get a single person
##Get title credits

#Reviews

##Create a review
##Update a review
##Delete a review

#Sync
##Get last activities

```shell
curl "https://api.mydramalist.com/sync/last_activities" \
  -H "Content-Type: application/json" \
  -H "mdl-api-key: [client_id]"
```

```json
{
  "all": "2019-04-03T22:53:52Z",
  "watching_at": "2019-04-03T22:53:52Z",
  "completed_at": "2019-04-03T22:53:52Z",
  "onhold_at": "0001-01-01T00:00:00Z",
  "plan_to_watch_at": "0001-01-01T00:00:00Z",
  "dropped_at": "0001-01-01T00:00:00Z",
  "not_interested_at": "0001-01-01T00:00:00Z",
  "rated_at": "2019-04-03T22:53:52Z"
}
```
##Get watchlist

```shell
curl "https://api.mydramalist.com/sync/mylist/[TYPE]" \
  -H "Content-Type: application/json" \
  -H "mdl-api-key: [client_id]"
```

```json
[
  {
    "list_id": 1,
    "episode_seen": 3,
    "rating": 0,
    "priority": 0,
    "times_rewatched": 0,
    "rewatch_value": 0,
    "date_start": "0000-00-00",
    "date_finish": "0000-00-00",
    "note": "testing2",
    "tags": "",
    "updated_at": "2019-04-04T06:29:03Z",
    "title": {
      "id": 25172,
      "title": "My Mister",
      "original_title": "나의 아저씨",
      "year": 2018,
      "episodes": 16,
      "rating": 9.2,
      "released": true,
      "ended": true,
      "type": "Drama",
      "country": "South Korea",
      "language": "Korean",
      "images": {
        "thumb": "https://i.mydramalist.com/X8rjwt.jpg",
        "medium": "https://i.mydramalist.com/X8rjwm.jpg",
        "poster": "https://i.mydramalist.com/X8rjwc.jpg"
      }
    }
  }
]
```

### Attributes
Attribute |  Type   | Description
--------- |  ------ | ------------
type      |  string | The type of the watchlist. Currently, we support `watchlist`, `completed`,`plantowatch`,`dropped`,`onhold`,`notinterested`


##Add to watchlist
##Remove from watchlist
