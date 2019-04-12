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
`Content-Type: application/json`

##Versioning

The API version is included in the base URL of the request. The current version is `v1`.

# Authentication
`GET https://api.mydramalist.com/oauth/authorize?response_type=code&client_id=[CLIENT_ID]&redirect_uri=[REDIRECT_URI]` 
`POST https://api.mydramalist.com/oauth/token?response_type=authorization_code&client_id=[CLIENT_ID]&client_secret=[CLIENT_SECRET]&redirect_uri=[REDIRECT_URI]&code=[AUTHORIZE_CODE]` 

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "mdl-api-key: [client_id]"
```

> Make sure to replace `[client_id]` with your API key.

MyDramaList uses API keys to allow access to the API. You can register a new MyDramaList API key at our [developer portal](http://example.com/developers).

MyDramaList expects for the API key to be included in all API requests to the server in a header that looks like the following:

`mdl-api-key: [client_id]`

`Authorization: Bearer [access_token]`

The bearer authorization header is scoped to an authorized platform user or application.

<aside class="notice">
You must replace <code>[client_id]</code> with your personal API key.
</aside>

# Titles


## Get a title

```shell
curl -X GET \
  https://api.mydramalist.com/titles/[id] \
  -H "Content-Type: application/json" \
  -H 'mdl-api-key: [client_id]'
```

> JSON response example:

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

`GET https://api.mydramalist.com/titles/[ID]`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The identifier of the title to be retrieved.

##Get title ratings
`GET https://api.mydramalist.com/titles/[ID]/ratings`
##Get all credits
`GET https://api.mydramalist.com/titles/[ID]/credits`
##Get all reviews
`GET https://api.mydramalist.com/titles/[ID]/reviews`
##Get related titles
`GET https://api.mydramalist.com/titles/[ID]/related`
##Get recently updates
`GET https://api.mydramalist.com/titles/updates/[START_DATE]` 
`e.g 2019-04-02`

#People

##Get a single person
`GET https://api.mydramalist.com/people/[ID]`
##Get title credits
`GET https://api.mydramalist.com/people/[ID]/credits`

#Reviews

##Create a review
##Update a review
##Delete a review

#Sync

##Get watchlist

```shell
curl "https://api.mydramalist.com/sync/mylist/[TYPE]" \
  -H "Content-Type: application/json" \
  -H "mdl-api-key: [client_id]"
```

> JSON response example:

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
type |  string | The type of the watchlist. Currently, we support `watchlist`, `completed`, `plantowatch`, `dropped`, `onhold`, `notinterested`


##Add to watchlist

```shell
curl -X POST \
  'https://api.mydramalist.com/sync/mylist' \
  -H "Content-Type: application/json" \
  -H 'authorization: Bearer [access_token]' \
  -H 'mdl-api-key: [client_id]' \
  --data '[
  {
    "list_id": 1,
    "episode_seen": 4,
    "rating": 0,
    "priority": 0,
    "times_rewatched": 0,
    "rewatch_value": 0,
    "date_start": "0000-00-00",
    "date_finish": "0000-00-00",
    "note": "testing2",
    "title": {
      "id": 25172,
      "title": "My Mister",
      "year": 2018,
      "type": "Drama",
      "country": "South Korea"
    }
  },
  {...}
]'
```
> JSON response example:

```json
{
  "success": {
    "titles": 1
  },
  "not_found": {
    "titles": [
      {
        "id": 191641111,
        "title": "Tokyo Ghoul"
      }
    ]
  }
}
```

###Watchlist object
Attribute | Type | Description
-------- | --------- | -------
list_id | integer |
episode_seen | integer |
rating | float |
priority | integer |
times_rewatched | integer |
rewatch_value | integer |
date_start | date |
date_finish | date |
note | string |
title | object |

###Title object
Attribute | Type | Description
-------- | --------- | -------
id  | integer |
title | string |
year  | integer |
type  | string |
country | string |


##Remove from watchlist

```shell
curl X DELETE \
  'http://api.mydramalist.com/sync/mylist' \
  -H 'authorization: Bearer [access_token]' \
  -H 'content-type: application/json' \
  -H 'mdl-api-key: [client_id]' \
  --data '[
      {
          "id": 12345
      },
      {
          "id": 25172
      }
    ]'
```
> JSON response example:

```json
{
  "deleted": {
    "titles": 1
  },
  "not_found": {
    "titles": [
      {
        "id": 12345
      }
    ]
  }
}
```

##Get last activities

```shell
curl "https://api.mydramalist.com/sync/last_activities" \
  -H "Content-Type: application/json" \
  -H "mdl-api-key: [client_id]"
```
> JSON response example:

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