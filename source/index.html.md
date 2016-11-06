---
title: TeamMood API Reference

language_tabs:
  - HTTP

toc_footers:
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:

search: true
---

# Introduction

Welcome to the TeamMood API! You can use our API to access TeamMood's app endpoints, which can get information on the data of your team.

# Authentication

TeamMood uses an API key to allow access to the API. 

Just grab your API key under the 'API Settings' menu item after [logging in on TeamMood](https://app.teammood.com/login).


# Moods

## Get All Moods

```HTTP
curl "https://app.teammood.com/api/{API_KEY}/moods"
```

> The above command returns JSON structured like this:

```json
{
   "teamName":"Demo",
   "tags":[
      "Group C",
      "Group B",
      "Group A"
   ],
   "days":[
      {
         "date":"Sunday, November 6, 2016",
         "today":true,
         "dateShort":"Sun 11/6/16",
         "nativeDate":1478386800000,
         "values":[
            {
               "mood":"good",
               "tags":[
                  "Group C"
               ],
               "comment":"A Good Day today!"
            },
            {
               "mood":"good",
               "tags":[
                  "Group C"
               ]
            },
            {
               "mood":"good",
               "tags":[
                  "Group A"
               ],
               "comment":"Some jokes around!"
            }
         ]
      },
      {
         "date":"Saturday, November 5, 2016",
         "today":false,
         "dateShort":"Sat 11/5/16",
         "nativeDate":1478300400000,
         "values":[
            {
               "mood":"average",
               "tags":[
                  "Group C"
               ],
               "comment":"Some days are better than others"
            }
         ]
      },
      {
         "date":"Friday, November 4, 2016",
         "today":false,
         "dateShort":"Fri 11/4/16",
         "nativeDate":1478214000000,
         "values":[
            {
               "mood":"average",
               "tags":[
                  "Group A"
               ],
               "comment":"Issues with my computer!"
            },
            {
               "mood":"average",
               "tags":[
                  "Group C"
               ]
            }
         ]
      }
   ]
}
```

This endpoint retrieves all moods of a team.

### HTTP Request

`GET https://app.teammood.com/api/{API_KEY}/moods`

<aside class="notice">By default, it retrieves all the moods for the last 30 days.</aside>

### Optional Query Parameters

Parameter | Description
--------- | -----------
start | The selection start date.
end | The selection end date.
since  | Retrieve the moods for the 'since' number of days.

### Results Attributes

Here are some not-so-obvious attributes.

Attribute | Description
--------- | -----------
mood | The value of the mood. Either `excellent`, `good`, `average`, `bad` or `hard`.
comment | Optional, the comment given by the user.

### Errors

The endpoint uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is incorrect
404 | Not Found -- The specified team could not be found, your API Key is wrong
418 | I'm a teapot
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.

### Example Query

Last moods for 10 days: [https://app.teammood.com/api/demo-en/moods?since=10](https://app.teammood.com/api/demo-en/moods?since=10)



