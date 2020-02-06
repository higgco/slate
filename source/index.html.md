---
title: Higg Public API Beta Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='mailto:support@higg.com'>Contact Support for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors
  - dictionary
  - scores
  - ghg
  - usage

search: true
---

# Introduction

Welcome to the Higg Public API Beta! You can use our API to access Higg Public API endpoints, which allows you to access module data that your account owns or that has been shared with your account.

We have language bindings in Shell (curl) and JavaScript. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

There are currently 2 available APIs and one API in planning

# Available APIs

## Bulk CSV API - PENDING REVISIONS - OFFLINE

The Bulk CSV API allows you to programmatically retrieve all module data that you own and that has been shared with you. The output is a CSV data stream that exactly matches what is available in the web portal for bulk download. The intent of the Bulk CSV API is not real-time interactions, it is for full data export/import use cases. Since this request can be 10's or 100's of megabytes in size, it is not useful for realtime interactions. 

This API uses cached data that is updates daily and is very performant, it just delivers very large datasets.

## Module Data API

The Module Data API is intended for real-time use cases, such as adding a specific data attribute to a scorecard (ex: total score) or for probing specific attributes across many modules. 

At its core it is a query API with various optional and required parameters. For maximum perfomance, this API has a few considerations to keep in mind:

* It is a paging API that returns a user defined number of results in each request. Its is the developers responsibility to make further calls to page through the remaining dataset.
* You can retrieve as many indicators as you require but be warned that these can grow the dataset tremendously which will slow-down API responsiveness. The preferred use case is very targeted data retrieval.
* Scores, ghg calcs, and resource usage data returned as indicators
* You can specify module type (fem2018, fem2019 etc), verification status, and module status, as filters.

Indicators are specified using the same column heading names as the bulk CSV. You can review the most commonly used attributes by viewing the data dictionary in the left navigation. Any deeper requirements should involve a Higg expert user who can help navigate those requirements to make sure you are retrieving the correct indicators.

## Adoption Data API

The Adoption Data API is still in planning but conceptually will consist of GET calls that allow you to retrieve adoption related data for your account, callback registrations that allow Higg systems to contact discrete endpoints when defined events occur, and PUT/POST calls that allow you to update your owned modules, shared modules, and shared account data with custom metadata relevant and specific to your account.

# Authentication

> To authorize, use this code:


```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "higg-api-token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJIaWdnLmNvbSIsImlhdCI6MTU3MDQxNzQ0MCwiZXhwIjoxNjAxOTUzNDQwLCJhdWQiOiJ3d3cuaGlnZy5vcmciLCJzdWIiOiJIaWdnLm9yZyIsIm5hbWUiOiJOYW1lIGZvciBrZXkgZm9yIHVzZXIgcmVmZXJlbmNlIiwiaWQiOiI1NjZhMzEyMC1lM2IwLTExZTktYmJjNC0yN2RmNjQ1MWJmMTAiLCJhY2NvdW50aWQiOiI1YTMwMDYzMjUwZTMzZDE3MTIzNzJiN2ZhOTlfZXhhbXBsZSJ9.K2xraHp4NTTGg5P8lJSmVx9oSF9JIscD9Wdp28nWXfg"
```

```javascript
# With XHR, you can just pass the correct header with each request. The same construct is true for a nodejs request object.
xhr.setRequestHeader("higg-api-token", "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJIaWdnLmNvbSIsImlhdCI6MTU3MDQxNzQ0MCwiZXhwIjoxNjAxOTUzNDQwLCJhdWQiOiJ3d3cuaGlnZy5vcmciLCJzdWIiOiJIaWdnLm9yZyIsIm5hbWUiOiJOYW1lIGZvciBrZXkgZm9yIHVzZXIgcmVmZXJlbmNlIiwiaWQiOiI1NjZhMzEyMC1lM2IwLTExZTktYmJjNC0yN2RmNjQ1MWJmMTAiLCJhY2NvdW50aWQiOiI1YTMwMDYzMjUwZTMzZDE3MTIzNzJiN2ZhOTlfZXhhbXBsZSJ9.K2xraHp4NTTGg5P8lJSmVx9oSF9JIscD9Wdp28nWXfg");
```

> Make sure to replace the JWT token with your provided API key.

The Higg Public API uses JWT based API keys to allow access to the API. Once you are API approved, you can create new Higg Public API keys in your account details screen. You can create unlimited API keys for different use cases and delete them when you want to disable access for those use cases.

The Higg Public API  expects for the API key to be included in all API requests to the server in a header that looks like the following:

`higg-api-token: {{provided jwt api key}}`

<aside class="notice">
You must replace <code>{{provided jwt api key}</code> with your provided API key.
</aside>

# Bulk CSV API - OFFLINE

## Get All FEM module data

```shell
curl -X GET \
  https://api-v2.production.higg.org/api/femcsv/5a30063250e33d1712372b7fa99_example \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'higg-api-token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJIaWdnLmNvbSIsImlhdCI6MTU3MDQxNzQ0MCwiZXhwIjoxNjAxOTUzNDQwLCJhdWQiOiJ3d3cuaGlnZy5vcmciLCJzdWIiOiJIaWdnLm9yZyIsIm5hbWUiOiJOYW1lIGZvciBrZXkgZm9yIHVzZXIgcmVmZXJlbmNlIiwiaWQiOiI1NjZhMzEyMC1lM2IwLTExZTktYmJjNC0yN2RmNjQ1MWJmMTAiLCJhY2NvdW50aWQiOiI1YTMwMDYzMjUwZTMzZDE3MTIzNzJiN2ZhOTlfZXhhbXBsZSJ9.K2xraHp4NTTGg5P8lJSmVx9oSF9JIscD9Wdp28nWXfg'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.production.higg.org/api/femcsv/5a30063250e33d1712372b7fa99_example',
  headers: 
     'cache-control': 'no-cache',
     'Content-Type': 'application/json',
     'higg-api-token': 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJIaWdnLmNvbSIsImlhdCI6MTU3MDQxNzQ0MCwiZXhwIjoxNjAxOTUzNDQwLCJhdWQiOiJ3d3cuaGlnZy5vcmciLCJzdWIiOiJIaWdnLm9yZyIsIm5hbWUiOiJOYW1lIGZvciBrZXkgZm9yIHVzZXIgcmVmZXJlbmNlIiwiaWQiOiI1NjZhMzEyMC1lM2IwLTExZTktYmJjNC0yN2RmNjQ1MWJmMTAiLCJhY2NvdW50aWQiOiI1YTMwMDYzMjUwZTMzZDE3MTIzNzJiN2ZhOTlfZXhhbXBsZSJ9.K2xraHp4NTTGg5P8lJSmVx9oSF9JIscD9Wdp28nWXfg' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> The above command returns the standard CSV bulk export format.

This endpoint retrieves all FEM module data as a CSV stream.

### HTTP Request

`GET https://api-v2.production.higg.org/api/femcsv/5a30063250e33d1712372b7fa99_example`

<aside class="success">
Remember to send the correct authentication header!
</aside>

## Get All FSLM module data

```shell
curl -X GET \
  https://api-v2.production.higg.org/api/fslmcsv/5a30063250e33d1712372b7fa99_example \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'higg-api-token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJIaWdnLmNvbSIsImlhdCI6MTU3MDQxNzQ0MCwiZXhwIjoxNjAxOTUzNDQwLCJhdWQiOiJ3d3cuaGlnZy5vcmciLCJzdWIiOiJIaWdnLm9yZyIsIm5hbWUiOiJOYW1lIGZvciBrZXkgZm9yIHVzZXIgcmVmZXJlbmNlIiwiaWQiOiI1NjZhMzEyMC1lM2IwLTExZTktYmJjNC0yN2RmNjQ1MWJmMTAiLCJhY2NvdW50aWQiOiI1YTMwMDYzMjUwZTMzZDE3MTIzNzJiN2ZhOTlfZXhhbXBsZSJ9.K2xraHp4NTTGg5P8lJSmVx9oSF9JIscD9Wdp28nWXfg'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api-v2.production.higg.org/api/fslmcsv/5a30063250e33d1712372b7fa99_example',
  headers: 
     'cache-control': 'no-cache',
     'Content-Type': 'application/json',
     'higg-api-token': 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJIaWdnLmNvbSIsImlhdCI6MTU3MDQxNzQ0MCwiZXhwIjoxNjAxOTUzNDQwLCJhdWQiOiJ3d3cuaGlnZy5vcmciLCJzdWIiOiJIaWdnLm9yZyIsIm5hbWUiOiJOYW1lIGZvciBrZXkgZm9yIHVzZXIgcmVmZXJlbmNlIiwiaWQiOiI1NjZhMzEyMC1lM2IwLTExZTktYmJjNC0yN2RmNjQ1MWJmMTAiLCJhY2NvdW50aWQiOiI1YTMwMDYzMjUwZTMzZDE3MTIzNzJiN2ZhOTlfZXhhbXBsZSJ9.K2xraHp4NTTGg5P8lJSmVx9oSF9JIscD9Wdp28nWXfg' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> The above command returns the standard CSV bulk export format.

This endpoint retrieves all FSLM module data as a CSV stream.

### HTTP Request

`GET https://api-v2.production.higg.org/api/fslmcsv/5a30063250e33d1712372b7fa99_example`

<aside class="success">
Remember to send the correct authentication header!
</aside>

# Module Data API

The Module Data API is a more complex query API with the following required and optional attributes. All attributes are sent as JSON.

IMPORTANT: The API allows the developer to create impossible to satisfy requests. For example, you can specify and account ID and a Module ID at the same time. If the Module ID is not owned by that account, it will not appear in the results since it is looking for the maximum match. In normal use this is not an issue, but be aware that the API does not detect or prevent this.

IMPORTANT: If a module self-assessment is not posted, it will still be returned in the result, but no question, scoring, usage or ghg data will be returned. This allows for adoption tracking but maintains the data privacy requirements.

IMPORTANT: If question level data is requested via include array, and it does NOT exist (invalid applicability path) the API will return 'null'. 

## Get FEM Module Data

Attribute | Argument Type | Required | Usage
-------------- | -------------- | -------------- | --------------
version | query | - | Specify which module category of data to retrieve (fem2017 | fem2018 | fem2019 | fslm | brm)
from | query | - | Integer value of where to start the window of results. If not specified, defaults to 0.
size | query | - | Integer value of how many results to return. If not specified, defaults to 10.
modules | query | - | Specify an array of specific module ID's (long Higg ID) to retrieve. If not specified, retrieves all modules of specified rfi_pid (subject to other query specifiers). Note that this can have unintuitive side-effects if you specify Module ID's that do not come from the specified Account ID's.
assessmentIds | query | - | Specify an array of specific account ID's to retrieve modules from. If not specified, retrieves all modules of specified rfi_pid (subject to other query specifiers). Note that this can have unintuitive side-effects if you specify Module ID's that do not come from the specified Account ID's.
accountIds | query | - | An array of account ID's (long Higg ID) to query modules for
include | filter | - | Specify an array of which indicators to retrieve. If not specified, ALL module data is returned. This can be VERY large. Indicator names are same as in bulk CSV and prefixed by 'questions.'. See example below and Data Dictionary for more information. 'scores', 'ghg', and 'usage' keywords enable the relevant data to be retrieved for each assessment. 
status | filter | - | An array of status to filter modules for
verified | filter | - | Filter for verified or unverified modules


```shell
curl -X POST \
  https://v2-api.production.higg.org/api/moduledata/fem \
  -H 'Content-Type: application/json' \
  -H 'higg-api-token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJIaWdnLmNvbSIsImlhdCI6MTU3MDQxNzQ0MCwiZXhwIjoxNjAxOTUzNDQwLCJhdWQiOiJ3d3cuaGlnZy5vcmciLCJzdWIiOiJIaWdnLm9yZyIsIm5hbWUiOiJOYW1lIGZvciBrZXkgZm9yIHVzZXIgcmVmZXJlbmNlIiwiaWQiOiI1NjZhMzEyMC1lM2IwLTExZTktYmJjNC0yN2RmNjQ1MWJmMTAiLCJhY2NvdW50aWQiOiI1YTMwMDYzMjUwZTMzZDE3MTIzNzJiN2ZhOTlfZXhhbXBsZSJ9.K2xraHp4NTTGg5P8lJSmVx9oSF9JIscD9Wdp28nWXfg' \
  -d '{
    "include": [
        "questions.sitecountry",
        "questions.sipfacilitytypetrim",
        "questions.table-ensourcenatgastracktable",
        "scores"
    ],
    "assessmentIds": ["ASSESSMENT_ID_1","ASSESSMENT_ID_2"],
    "accountIds":["ACCCOUNT_ID_1","ACCCOUNT_ID_2"],
    "version": "fem2018",
    "verified": true,
    "status": ["ASC","VRF"],
    "from": 0,
	"size": 10
}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://v2-api.production.higg.org/api/moduledata/fem',
  headers: 
   { 'Content-Type': 'application/json',
   'higg-api-token': 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJIaWdnLmNvbSIsImlhdCI6MTU3MDQxNzQ0MCwiZXhwIjoxNjAxOTUzNDQwLCJhdWQiOiJ3d3cuaGlnZy5vcmciLCJzdWIiOiJIaWdnLm9yZyIsIm5hbWUiOiJOYW1lIGZvciBrZXkgZm9yIHVzZXIgcmVmZXJlbmNlIiwiaWQiOiI1NjZhMzEyMC1lM2IwLTExZTktYmJjNC0yN2RmNjQ1MWJmMTAiLCJhY2NvdW50aWQiOiI1YTMwMDYzMjUwZTMzZDE3MTIzNzJiN2ZhOTlfZXhhbXBsZSJ9.K2xraHp4NTTGg5P8lJSmVx9oSF9JIscD9Wdp28nWXfg' },
  body: 
   {
    "include": [
        "questions.sitecountry",
        "questions.sipfacilitytypetrim",
        "questions.table-ensourcenatgastracktable",
        "scores"
    ],
    "assessmentIds": ["ASSESSMENT_ID_1","ASSESSMENT_ID_2"],
    "accountIds":["ACCCOUNT_ID_1","ACCCOUNT_ID_2"],
    "version": "fem2018",
    "verified": true,
    "status": ["ASC","VRF"],
    "from": 0,
	"size": 10
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

> The above command returns the following JSON data. 

The Module Data API allows for retrieval of all assessment types (FEM, FSLM, BRM) but each request is specific to an rfi_pid. This is to ensure uniformity in indicator retrieval and index performance.

### HTTP Request

`https://v2-api.production.higg.org/api/moduledata/fem`

See examples for JSON argument usage

The result set is in the following format:

```json
{
    "from": 0,
    "size": 1,
    "total": 643,
    "assessments": [
        {
            "id": "REDACTED",
            "statusHistory": {
                "ASI": "",
                "ASC": "",
                "VRP": "",
                "VRC": "",
                "VRF": "",
                "VRD": "",
                "VRI": "",
                "ASD": ""
            },
            "status": "VRF",
            "version": "fem2017",
            "accountId": "REDACTED",
            "accountName": "REDACTED",
            "sacId": "REDACTED",
            "country": "Thailand",
            "selfPosted": true,
            "verifiedPosted": true,
            "verified": true,
            "scores": {
                "site": {
                    "scores": {},
                    "levels": {
                        "1": 0,
                        "2": null,
                        "3": null
                    },
                    "levelsOpen": [
                        1
                    ],
                    "levelsAchieved": [],
                    "applicability": null,
                    "total": 0
                },
                "water": {
                    "scores": {
                        "watsources": {
                            "score": 25,
                            "level": 1
                        },
                        "watbaselineopt": {
                            "score": 0,
                            "level": 2
                        },
                        "wathighestuse": {
                            "score": 10,
                            "level": 2
                        },
                        "wattargetopt": {
                            "score": 0,
                            "level": 2
                        },
                        "watimproveplan": {
                            "score": 5,
                            "level": 2
                        },
                        "watimproveopt": {
                            "score": 0,
                            "level": 2
                        },
                        "watbalanceanalysis": {
                            "score": 25,
                            "level": 3
                        }
                    },
                    "levels": {
                        "1": 25,
                        "2": 15,
                        "3": 25
                    },
                    "levelsOpen": [
                        1,
                        2,
                        3
                    ],
                    "levelsAchieved": [
                        1,
                        3
                    ],
                    "applicability": "AppWater001",
                    "total": 65
                },
                "energy": {
                    "scores": {
                        "ensourcetrackopt": {
                            "score": 50,
                            "level": 1
                        },
                        "enbaselinesource": {
                            "score": 0,
                            "level": 2
                        },
                        "enhighestuse": {
                            "score": 10,
                            "level": 2
                        },
                        "entargetssource": {
                            "score": 0,
                            "level": 2
                        },
                        "enimproveplan": {
                            "score": 0,
                            "level": 2
                        },
                        "enimprovesource": {
                            "score": 0,
                            "level": 2
                        },
                        "enscope3ghg": {
                            "score": 0,
                            "level": 3
                        }
                    },
                    "levels": {
                        "1": 50,
                        "2": 10,
                        "3": null
                    },
                    "levelsOpen": [
                        1,
                        2,
                        3
                    ],
                    "levelsAchieved": [
                        1
                    ],
                    "applicability": null,
                    "total": 60
                },
                "waste": {
                    "scores": {
                        "wstsourcenh": {
                            "score": 3.5714285714285716,
                            "level": 1
                        },
                        "wstsourceh": {
                            "score": 3.5714285714285716,
                            "level": 1
                        },
                        "wstsegregatestreams": {
                            "score": 3.5714285714285716,
                            "level": 1
                        },
                        "wsthstorage": {
                            "score": 3.5714285714285716,
                            "level": 1
                        },
                        "wstnhstorage": {
                            "score": 3.5714285714285716,
                            "level": 1
                        },
                        "wstpolhtml": {
                            "score": 3.5714285714285716,
                            "level": 1
                        },
                        "wsthtrain": {
                            "score": 3.5714285714285716,
                            "level": 1
                        },
                        "wstbaseline": {
                            "score": 0,
                            "level": 2
                        },
                        "wstbaselinedisp": {
                            "score": 0,
                            "level": 2
                        },
                        "wsttarget": {
                            "score": 0,
                            "level": 2
                        },
                        "wsttargetdisp": {
                            "score": 0,
                            "level": 2
                        },
                        "wstredimpplan": {
                            "score": 7.142857142857143,
                            "level": 2
                        },
                        "wstredimp2018": {
                            "score": 0,
                            "level": 2
                        },
                        "wstredimpdisp": {
                            "score": 0,
                            "level": 2
                        },
                        "wsthazdispvalidate": {
                            "score": 8.333333333333334,
                            "level": 3
                        },
                        "wstdispzerowaste": {
                            "score": 0,
                            "level": 3
                        },
                        "wstdispupcycle": {
                            "score": 0,
                            "level": 3
                        }
                    },
                    "levels": {
                        "1": 25.000000000000004,
                        "2": 7.142857142857143,
                        "3": 8.333333333333334
                    },
                    "levelsOpen": [
                        1,
                        2,
                        3
                    ],
                    "levelsAchieved": [
                        1
                    ],
                    "applicability": null,
                    "total": 40.47619047619048
                },
                "wastewater": {
                    "scores": {
                        "wwtrack": {
                            "score": 8.333333333333334,
                            "level": 1
                        },
                        "wwemergplan": {
                            "score": 8.333333333333334,
                            "level": 1
                        },
                        "wwhsludgedisposal": {
                            "score": 0,
                            "level": 1
                        },
                        "wwstandard": {
                            "score": 50,
                            "level": 2
                        },
                        "wwrecycle": {
                            "score": 0,
                            "level": 3
                        }
                    },
                    "levels": {
                        "1": 16.666666666666668,
                        "2": 50,
                        "3": 0
                    },
                    "levelsOpen": [
                        1,
                        2,
                        3
                    ],
                    "levelsAchieved": [
                        2
                    ],
                    "applicability": "AppWW001",
                    "total": 66.66666666666667
                },
                "chemicals": {
                    "scores": {
                        "chemtrack": {
                            "score": 1.92,
                            "level": 1
                        },
                        "chemsds": {
                            "score": 1.92,
                            "level": 1
                        },
                        "chemtraining": {
                            "score": 1.92,
                            "level": 1
                        },
                        "chememergplan": {
                            "score": 1.92,
                            "level": 1
                        },
                        "chemsafetyequip": {
                            "score": 1.92,
                            "level": 1
                        },
                        "chemhazardsign": {
                            "score": 1.92,
                            "level": 1
                        },
                        "chempurchasereq": {
                            "score": 1.92,
                            "level": 1
                        },
                        "chemhealthprogram": {
                            "score": 1.92,
                            "level": 1
                        },
                        "chemstorage": {
                            "score": 0.96,
                            "level": 1
                        },
                        "chemtrainingRSL": {
                            "score": 1.92,
                            "level": 1
                        },
                        "chemprocessidentifyRSL": {
                            "score": 1.92,
                            "level": 1
                        },
                        "chemprocessmonitorRSL": {
                            "score": 0,
                            "level": 1
                        },
                        "chemtraceinventory": {
                            "score": 1.92,
                            "level": 1
                        },
                        "chemimproveplan": {
                            "score": 0,
                            "level": 2
                        },
                        "chemreduceplan": {
                            "score": 0,
                            "level": 2
                        },
                        "chemsourcelist": {
                            "score": 0,
                            "level": 2
                        },
                        "chemcollabalternatives": {
                            "score": 0,
                            "level": 3
                        },
                        "chemtracelotnumber": {
                            "score": 0,
                            "level": 3
                        },
                        "chemanalysishumanenv": {
                            "score": 0,
                            "level": 3
                        },
                        "chemanalysislifecycle": {
                            "score": 0,
                            "level": 3
                        },
                        "chemdocumentedqa": {
                            "score": 0,
                            "level": 3
                        },
                        "chemcontractorsRSL": {
                            "score": 0,
                            "level": 3
                        },
                        "chemdocumentedgoals": {
                            "score": 0,
                            "level": 3
                        }
                    },
                    "levels": {
                        "1": 22.080000000000005,
                        "2": null,
                        "3": null
                    },
                    "levelsOpen": [
                        1
                    ],
                    "levelsAchieved": [],
                    "applicability": "AppChem001",
                    "total": 22.080000000000005
                },
                "airemissions": {
                    "scores": {
                        "airsourceopstrack": {
                            "score": 5,
                            "level": 1
                        },
                        "airsourceprodtrack": {
                            "score": 5,
                            "level": 1
                        },
                        "airsourcerefrignew": {
                            "score": 5,
                            "level": 1
                        },
                        "aircontroldevopshtml": {
                            "score": 5,
                            "level": 1
                        },
                        "aircontroldevprodhtml": {
                            "score": 5,
                            "level": 1
                        },
                        "airbeyondpermit": {
                            "score": 0,
                            "level": 2
                        },
                        "airimplementprocess": {
                            "score": 12.5,
                            "level": 3
                        }
                    },
                    "levels": {
                        "1": 25,
                        "2": 0,
                        "3": 12.5
                    },
                    "levelsOpen": [
                        1,
                        2,
                        3
                    ],
                    "levelsAchieved": [
                        1,
                        3
                    ],
                    "applicability": "AppAir005",
                    "total": 37.5
                },
                "ems": {
                    "scores": {
                        "emsmgmt": {
                            "score": 4.166666666666667,
                            "level": 1
                        },
                        "emsstrategy": {
                            "score": 4.166666666666667,
                            "level": 1
                        },
                        "emsopsimpact": {
                            "score": 4.166666666666667,
                            "level": 1
                        },
                        "emspermitstatus": {
                            "score": 4.166666666666667,
                            "level": 1
                        },
                        "emsregulationsystem": {
                            "score": 4.166666666666667,
                            "level": 1
                        },
                        "emsequipmaintain": {
                            "score": 4.166666666666667,
                            "level": 1
                        },
                        "emsstrategyreview": {
                            "score": 25,
                            "level": 2
                        },
                        "emsmgmtcompetence": {
                            "score": 25,
                            "level": 2
                        },
                        "emsstrategyawareness": {
                            "score": 6.25,
                            "level": 3
                        },
                        "emshiggindexsubcontract": {
                            "score": 6.25,
                            "level": 3
                        },
                        "emsengagelocal": {
                            "score": 6.25,
                            "level": 3
                        },
                        "emshiggindexupstream": {
                            "score": 0,
                            "level": 3
                        }
                    },
                    "levels": {
                        "1": 25.000000000000004,
                        "2": 50,
                        "3": 18.75
                    },
                    "levelsOpen": [
                        1,
                        2,
                        3
                    ],
                    "levelsAchieved": [
                        1,
                        2
                    ],
                    "applicability": "AppEMS001",
                    "total": 93.75
                },
                "finalScore": 55.06755102040817,
                "averageLevelAchieved": 0.2857142857142857,
                "sipvalidoperatinglicense": true
            },
            "questions": {
                "sitecountry": {
                    "value": "China",
                    "corrected": "China",
                    "selection": "",
                    "flag": false,
                    "data": ""
                },
                "sipfacilitytypetrim": {
                    "value": "No",
                    "corrected": "No",
                    "selection": "",
                    "flag": false,
                    "data": ""
                },
                "table-ensourcenatgastracktable": null
            }
        }
    ]
}
```
<aside class="success">
Remember to send the correct authentication header!
</aside>
<aside class="success">
Remember to send arguments as JSON!
</aside>

## Get FSLM Module Data

Attribute | Argument Type | Required | Usage
-------------- | -------------- | -------------- | --------------
version | query | - | Specify which module category of data to retrieve (fem2017 | fem2018 | fem2019 | fslm | brm)
from | query | - | Integer value of where to start the window of results. If not specified, defaults to 0.
size | query | - | Integer value of how many results to return. If not specified, defaults to 10.
modules | query | - | Specify an array of specific module ID's (long Higg ID) to retrieve. If not specified, retrieves all modules of specified rfi_pid (subject to other query specifiers). Note that this can have unintuitive side-effects if you specify Module ID's that do not come from the specified Account ID's.
assessmentIds | query | - | Specify an array of specific account ID's to retrieve modules from. If not specified, retrieves all modules of specified rfi_pid (subject to other query specifiers). Note that this can have unintuitive side-effects if you specify Module ID's that do not come from the specified Account ID's.
accountIds | query | - | An array of account ID's (long Higg ID) to query modules for
include | filter | - | Specify an array of which indicators to retrieve. If not specified, ALL data is returned. This can be VERY large. Indicator names are same as in bulk CSV and prefixed by 'questions.'  See Data Dictionary for more information.
status | filter | - | An array of status to filter modules for
verified | filter | - | Filter for verified or unverified modules


```shell
curl -X POST \
  https://v2-api.production.higg.org/api/moduledata/fslm \
  -H 'Content-Type: application/json' \
  -H 'higg-api-token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJIaWdnLmNvbSIsImlhdCI6MTU3MDQxNzQ0MCwiZXhwIjoxNjAxOTUzNDQwLCJhdWQiOiJ3d3cuaGlnZy5vcmciLCJzdWIiOiJIaWdnLm9yZyIsIm5hbWUiOiJOYW1lIGZvciBrZXkgZm9yIHVzZXIgcmVmZXJlbmNlIiwiaWQiOiI1NjZhMzEyMC1lM2IwLTExZTktYmJjNC0yN2RmNjQ1MWJmMTAiLCJhY2NvdW50aWQiOiI1YTMwMDYzMjUwZTMzZDE3MTIzNzJiN2ZhOTlfZXhhbXBsZSJ9.K2xraHp4NTTGg5P8lJSmVx9oSF9JIscD9Wdp28nWXfg' \
  -d '{
    "include": [
        "questions.FP-BI-3",
        "questions.FP-BS-10",
        "questions.FP-BS-4",
        "scores"
    ],
    "assessmentIds": ["ASSESSMENT_ID_1","ASSESSMENT_ID_2"],
    "accountIds":["ACCCOUNT_ID_1","ACCCOUNT_ID_2"],
    "version": "fslm",
    "verified": true,
    "status": ["ASC","VRF"],
    "from": 0,
	"size": 10
}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://v2-api.production.higg.org/api/moduledata/fslm',
  headers: 
   { 'Content-Type': 'application/json',
   'higg-api-token': 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJIaWdnLmNvbSIsImlhdCI6MTU3MDQxNzQ0MCwiZXhwIjoxNjAxOTUzNDQwLCJhdWQiOiJ3d3cuaGlnZy5vcmciLCJzdWIiOiJIaWdnLm9yZyIsIm5hbWUiOiJOYW1lIGZvciBrZXkgZm9yIHVzZXIgcmVmZXJlbmNlIiwiaWQiOiI1NjZhMzEyMC1lM2IwLTExZTktYmJjNC0yN2RmNjQ1MWJmMTAiLCJhY2NvdW50aWQiOiI1YTMwMDYzMjUwZTMzZDE3MTIzNzJiN2ZhOTlfZXhhbXBsZSJ9.K2xraHp4NTTGg5P8lJSmVx9oSF9JIscD9Wdp28nWXfg' },
  body: 
   {
    "include": [
        "questions.FP-BI-3",
        "questions.FP-BS-10",
        "questions.FP-BS-4",
        "scores"
    ],
    "assessmentIds": ["ASSESSMENT_ID_1","ASSESSMENT_ID_2"],
    "accountIds":["ACCCOUNT_ID_1","ACCCOUNT_ID_2"],
    "version": "fslm",
    "verified": true,
    "status": ["ASC","VRF"],
    "from": 0,
	"size": 10
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

> The above command returns the following JSON data. 

### HTTP Request

`https://v2-api.production.higg.org/api/moduledata/fsm`

See examples for JSON argument usage

The result set is in the following format:

```json
{
    "from": 0,
    "size": 1,
    "total": 36,
    "assessments": [
        {
            "id": "REDACTED",
            "statusHistory": {
                "ASI": "",
                "ASC": "",
                "VRP": "",
                "VRC": "2019/03/05",
                "VRF": "2019/03/05",
                "VRD": "",
                "VRI": "",
                "ASD": ""
            },
            "status": "VRF",
            "version": "fslm",
            "accountId": "REDACTED",
            "accountName": "REDACTED",
            "sacId": "REDACTED",
            "country": "Sri Lanka",
            "selfPosted": true,
            "verifiedPosted": true,
            "verified": true,
            "questions": {
                "FP-BI-3": {
                    "value": "REDACTED",
                    "corrected": "REDACTED",
                    "selection": "Updated during Verification",
                    "flag": false,
                    "data": "REDACTED",
                    "legal": ""
                },
                "FP-BS-10": {
                    "value": 25922,
                    "corrected": null,
                    "selection": "Accurate",
                    "flag": false,
                    "data": "",
                    "legal": ""
                },
                "FP-BS-4": {
                    "value": "Warehouses are separate buildings",
                    "corrected": null,
                    "selection": "Accurate",
                    "flag": false,
                    "data": "Finished goods warehouse is in a separate building & raw material stores is located with in the production building No 01. ",
                    "legal": ""
                }
            }
        }
    ]
}
```
<aside class="success">
Remember to send the correct authentication header!
</aside>
<aside class="success">
Remember to send arguments as JSON!
</aside>

# Adoption Data API

Pending final implementation