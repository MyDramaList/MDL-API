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
`GET https://api.mydramalist.com/v1/oauth/authorize?response_type=code&client_id=[CLIENT_ID]&redirect_uri=[REDIRECT_URI]` 
`POST https://api.mydramalist.com/v1/oauth/token?response_type=authorization_code&client_id=[CLIENT_ID]&client_secret=[CLIENT_SECRET]&redirect_uri=[REDIRECT_URI]&code=[AUTHORIZE_CODE]` 

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

# Search
Parameter | Description
--------- | -----------
q | Query

## Search Titles
`POST https://api.mydramalist.com/v1/search/titles`

# Titles


## Get a title

```shell
curl -X GET \
  https://api.mydramalist.com/v1/titles/[id] \
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
    "thumb": "...",
    "medium": "...",
    "poster": "..."
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

This endpoint retrieves a specific TV show or movie.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://api.mydramalist.com/v1/titles/[ID]`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The identifier of the title to be retrieved.

##Get title ratings

```shell
curl -X GET \
  https://api.mydramalist.com/v1/titles/[id]/ratings \
  -H "Content-Type: application/json" \
  -H 'mdl-api-key: [client_id]'
```

> JSON response example:

```json
{
  "rating": 8,
  "votes": 4207,
  "distribution": {
    "9.5": 324,
    "4.0": 31,
    "6.5": 166,
    "7.0": 431,
    "7.5": 455,
    "4.5": 27,
    "10.0": 491,
    "1.5": 2,
    "2.0": 13,
    "2.5": 10,
    "3.0": 16,
    "8.0": 765,
    "8.5": 641,
    "9.0": 620,
    "3.5": 10,
    "5.0": 93,
    "5.5": 59,
    "6.0": 175,
    "1.0": 24
  }
}
```
Get the ratings distrubtion for a TV show or movie.

`GET https://api.mydramalist.com/v1/titles/[ID]/ratings`

##Get all credits

```shell
curl -X GET \
  https://api.mydramalist.com/v1/titles/[id]/credits \
  -H "Content-Type: application/json" \
  -H 'mdl-api-key: [client_id]'
```

> JSON response example:

```json
{
  "cast": [
    {
      "id": 5043,
      "name": "Lee Jun Ho",
      "slug": "5043-lee-jun-ho",
      "images": {
        "thumb": "...",
        "poster": "..."
      },
      "character_name": "Seo Poong",
      "role": "Main Role"
    },
    {
      "id": 181,
      "name": "Jang Hyuk",
      "slug": "181-jang-hyuk",
      "images": {
        "thumb": "...",
        "poster": "..."
      },
      "character_name": "Doo Chil Seong",
      "role": "Main Role"
    }
]
```
Get the credits for a TV show or movie.

`GET https://api.mydramalist.com/v1/titles/[ID]/credits`

##Get all reviews

```shell
curl -X GET \
  https://api.mydramalist.com/v1/titles/[id]/reviews \
  -H "Content-Type: application/json" \
  -H 'mdl-api-key: [client_id]'
```

> JSON response example:

```json
[
  {
    "id": 47125,
    "ratings": {
      "story": 7,
      "acting": 8.5,
      "music": 8.5,
      "rewatch": 8.5,
      "overall": 8.5
    },
    "headline": "",
    "review": "Pellentesque dapibus hendrerit tortor. Maecenas ullamcorper...",
    "version": 4,
    "upvotes": 0,
    "total_votes": 0,
    "completed": true,
    "dropped": false,
    "spoiler": false,
    "lang_iso": "en-US",
    "comments": 19,
    "voted": 0,
    "episodes": 1,
    "episodes_seen": 1,
    "author": {
      "username": "Dummy",
      "display_name": "Dummy",
      "avatar_url": "..."
    },
    "title": {
      "id": 24640,
      "slug": "/24640-test-content",
      "title": "Test Content",
      "type": "Movie",
      "year": 2018,
      "images": {
        "thumb": "...",
        "medium": "...",
        "poster": "..."
      }
    },
    "created_at": "2019-05-13T08:09:55Z"
  }
]
```
Get the reviews for a TV show or movie.

`GET https://api.mydramalist.com/v1/titles/[ID]/reviews`
##Get related titles

```shell
curl -X GET \
  https://api.mydramalist.com/v1/titles/[id]/related \
  -H "Content-Type: application/json" \
  -H 'mdl-api-key: [client_id]'
```

> JSON response example:

```json
[
  {
    "id": 50319,
    "title": "Unknown Number",
    "original_title": "时空来电",
    "year": 2019,
    "rating": 9.1,
    "permalink": "/50319-unknown-number",
    "type": "Drama",
    "language": "Chinese",
    "related_type": "Remake",
    "images": {
      "thumb": "...",
      "medium": "...",
      "poster": "..."
    }
  }
]
```

Get a list of related titles for a TV show or movie.

`GET https://api.mydramalist.com/v1/titles/[ID]/related`

##Get recently updates

```shell
curl -X GET \
  https://api.mydramalist.com/v1/titles/updates/[START_DATE] \
  -H "Content-Type: application/json" \
  -H 'mdl-api-key: [client_id]'
```

> JSON response example:

```json
[
  {
    "id": 1988,
    "title": "Tenkosei: Sayonara Anata",
    "updated_at": "2019-04-01T09:50:10Z"
  },
  {
    "id": 7703,
    "title": "Houkago",
    "updated_at": "2019-04-01T09:50:14Z"
  },
  {
    "id": 16169,
    "title": "Morrasoom Sawat",
    "updated_at": "2019-04-01T09:50:27Z"
  }
]
```

Get a list of recently updates TV shows or movies. 

`GET https://api.mydramalist.com/v1/titles/updates/[START_DATE]` 
`e.g 2019-04-02`

#People

##Get a person details

```shell
curl -X GET \
  https://api.mydramalist.com/v1/people/[ID] \
  -H "Content-Type: application/json" \
  -H 'mdl-api-key: [client_id]'
```

> JSON response example:

```json
{
  "id": 972,
  "name": "Im Yoon Ah",
  "first_name": "Yoon Ah",
  "family_name": "Im",
  "original_name": "임윤아",
  "biography": "Im Yoon Ah, commonly stylized as Yoona, is a popular South Korean pop singer, dancer, actress, model and spokesmodel. She is a member of the Korean girl group Girls' Generation and is known as the center-girl, lead dancer and sub-vocalist of the group. Yoona made her debut as a singer along with Girls' Generation on August 5, 2007. She made her debut as an actress in the 2007 Korean drama, 9 Ends, 2 Outs. \nIn January 2014, Yoona and actor Lee Seung Gi were confirmed to be in a relationship since September 2013. On the 13 of August 2015, both stars confirmed they broke up after dating for a year and nine months due to busy schedules.",
  "permalink": "https://mydramalistcom/people/972-im-yoon-ah",
  "slug": "people/972-im-yoon-ah",
  "birthday": "1990-05-30",
  "dod": "0000-00-00",
  "nationality": "South Korean",
  "thumbnail": "",
  "images": {
    "thumb": "...",
    "medium": "...",
    "poster": "..."
  }
}
```

Get the primary person details by id.

`GET https://api.mydramalist.com/v1/people/[ID]`
##Get title credits

```shell
curl -X GET \
  https://api.mydramalist.com/v1/people/[ID]/credits \
  -H "Content-Type: application/json" \
  -H 'mdl-api-key: [client_id]'
```

> JSON response example:

```json
{
  "cast": [
    {
      "role": "Main Role",
      "also_known_as": "Seo Yoo Jin",
      "title": {
        "id": 242,
        "slug": "/242-cinderella-man",
        "title": "Cinderella Man",
        "original_title": "신데렐라 맨",
        "year": 2009,
        "episodes": 16,
        "rating": 6.7,
        "type": "Drama",
        "language": "Korean",
        "images": {
          "thumb": "...",
          "medium": "...",
          "poster": "..."
        }
      }
    },
    {
      "role": "Main Role",
      "also_known_as": "Jang Sae Byuk",
      "title": {
        "id": 451,
        "slug": "/451-you-are-my-destiny",
        "title": "You Are My Destiny",
        "original_title": "너는 내 운명",
        "year": 2008,
        "episodes": 178,
        "rating": 7,
        "type": "Drama",
        "language": "Korean",
        "images": {
          "thumb": "...",
          "medium": "...",
          "poster": "..."
        }
      }
    },
  ],
  crew: []
}
```
Get the TV show or movie credits for a person.

`GET https://api.mydramalist.com/v1/people/[ID]/credits`

#Reviews

##Get a review

```shell
curl -X GET \
  https://api.mydramalist.com/v1/reviews/[ID] \
  -H "Content-Type: application/json" \
  -H 'mdl-api-key: [client_id]'
```

> JSON response example:

```json
{
  "id": 40016,
  "ratings": {
    "story": 9.5,
    "acting": 9,
    "music": 9,
    "rewatch": 9.5,
    "overall": 9
  },
  "headline": "Amazing drama!",
  "review": "Nullam tincidunt adipiscing enim. Phasellus magna...",
  "version": 5,
  "upvotes": 2,
  "total_votes": 2,
  "completed": false,
  "dropped": true,
  "spoiler": false,
  "lang_iso": "en-US",
  "comments": 3,
  "voted": 1,
  "episodes": 17,
  "episodes_seen": 9,
  "author": {
    "username": "Dummy",
    "display_name": "Dummy",
    "avatar_url": "..."
  },
  "title": {
    "id": 29385,
    "slug": "/29385-test-title-22341",
    "title": "Test Content 2",
    "type": "Drama",
    "year": 2015,
    "images": {
      "thumb": "...",
      "medium": "...",
      "poster": "..."
    }
  },
  "created_at": "2018-08-08T01:36:33Z"
}
```
Get a review details by ID.

`GET https://api.mydramalist.com/v1/reviews/[ID]`

##Create a review

```shell
curl -X POST \
  'https://api.mydramalist.com/v1/reviews' \
  -H "Content-Type: application/json" \
  -H 'authorization: Bearer [access_token]' \
  -H 'mdl-api-key: [client_id]' \
  --data '{
"completed": true,
"dropped": false,
"episodes_seen": 1,
"headline": null,
"parent_id": 24640,
"lang_iso": "en-US",
"ratings": {
  "story": 9, 
  "acting": 8.5, 
  "music": 9, 
  "rewatch": 8.5, 
  "overall": 9.5
},
"review": "Donec id justo. Suspendisse eanim turpis, dictum sed, iaculis a, condimentum nec, nisi. Fusce fermentum odio nec arcu. Nullam sagittis. Cras dapibus.\n\nEtiam vitae tortor. Suspendisse feugiat. Phasellus dolor. Aenean leo ligula, porttitor eu, consequat vitae, eleifend ac, enim. Fusce a quam.\n\nDonec orci lectus, aliquam ut, faucibus non, euismod id, nulla. Nunc nulla. Vivamus elementum semper nisi. \n\nPellentesque egestas, neque sit amet convallis pulvinar, justo nulla eleifend augue, ac auctor orci leo non est. Quisque ut nisi.",
"spoiler": false
}'
```

Post a review for a TV show or movie. The `parent_id` is field is required for the TV shows or movie.

###Review object
Attribute | Type | Description
-------- | --------- | -------
completed | boolean |
dropped | boolean |
episodes_seen | integer |
headline | string |
parent_id | integer |
lang_iso | string |
ratings | ratings object | 
review | string |
spoiler | boolean |

###Ratings object
Attribute | Type | Description
-------- | --------- | -------
story | float  
acting | float  
music | float  
rewatch | float  
overall | float  

`POST https://api.mydramalist.com/v1/reviews`

##Update a review


```shell
curl -X PATCH \
  'https://api.mydramalist.com/v1/reviews/[ID]' \
  -H "Content-Type: application/json" \
  -H 'authorization: Bearer [access_token]' \
  -H 'mdl-api-key: [client_id]' \
  --data '{
"completed": true,
"dropped": false,
"episodes_seen": 1,
"headline": null,
"id": 41568,
"lang_iso": "es",
"ratings": {
  "story": 9, 
  "acting": 8.5, 
  "music": 9, 
  "rewatch": 8.5, 
  "overall": 9.5
},
"review": "Donec id justo. Suspendisse eanim turpis, dictum sed, iaculis a, condimentum nec, nisi. Fusce fermentum odio nec arcu. Nullam sagittis. Cras dapibus.\n\nEtiam vitae tortor. Suspendisse feugiat. Phasellus dolor. Aenean leo ligula, porttitor eu, consequat vitae, eleifend ac, enim. Fusce a quam.\n\nDonec orci lectus, aliquam ut, faucibus non, euismod id, nulla. Nunc nulla. Vivamus elementum semper nisi. \n\nPellentesque egestas, neque sit amet convallis pulvinar, justo nulla eleifend augue, ac auctor orci leo non est. Quisque ut nisi.",
"spoiler": false
}'
```

Update a single review. The OAuth user must match the author of the review in order to update it.

`PATCH https://api.mydramalist.com/v1/reviews/[ID]`

##Delete a review

```shell
curl X DELETE \
  'http://api.mydramalist.com/reviews/[ID]' \
  -H 'authorization: Bearer [access_token]' \
  -H 'content-type: application/json' \
  -H 'mdl-api-key: [client_id]' 
```

Delete a single review. The OAuth user must match the author of the review in order to delete it. 

`DELETE https://api.mydramalist.com/v1/reviews/[ID]`

#Genres

##Get genres
`GET https://api.mydramalist.com/v1/genres`

#Sync

##Get watchlist

```shell
curl "https://api.mydramalist.com/v1/sync/mylist/[TYPE]" \
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
        "thumb": "...",
        "medium": "...",
        "poster": "..."
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
  'https://api.mydramalist.com/v1/sync/mylist' \
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
curl "https://api.mydramalist.com/v1/sync/last_activities" \
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

#Users
##Get user settings
`GET https://api.mydramalist.com/v1/users/settings`