# Guide for the API

(created 2023-01-27 using v0.2) 
{: class="guideCreated"}

## Introduction

The **A**pplication **P**rogramming **I**nterface (API) is a core feature of the OpenStduyBuilder, as integrations with other tools are key to enable fully automated processes. The heart of the MDR is the graph database which is a Neo4j database. There could be directly commands on the database, which might be used for standards and data import. But APIs allow for more controlled operations on the database. The OpenStudyBuilder solution - so the web application - is fully working on the APIs available. 

The OpenStudyBuilder API allows you for example to:

- GET a list of all studies
- GET information of one study
- PATCH information for one study
- GET a list of all ODM templates (CRF templates)
- GET a list of all ODM forms
- Receive an ODM XML for a given template

There are really many endpoints available. All tasks which are performed by the OpenStudyBuilder solution are done through these APIs. There are

## API Definition

!!! quote

    An application programming interface (API) is a way for two or more computer programs to communicate with each other. It is a type of software interface, offering a service to other pieces of software. A document or standard that describes how to build or use such a connection or interface is called an API specification.[1]

[1] Wikipedia entry for API, [https://en.wikipedia.org/wiki/API](https://en.wikipedia.org/wiki/API)
{: class="imageDescription"}

![Schema for API](./img/guide_api_intro1.png)
{: class="imageParagraph"}

Figure 1: Simplyfied API process
{: class="imageDescription"}

## OpenStudyBuilder API Design

In the OpenStudyBuilder the API usage is more complex. APIs are not only available for the OpenStudyBuilder, but are utilized by many other tools as these make the communication between computer programs much easier. 

![OpenStudyBuilder Conceptual Architecture](./img/studyBuilderDesign.png)
{: class="imageParagraph"}

Figure 2: OpenStudyBuilder Conceptual Architecture
{: class="imageDescription"}

Let us start on the left side. The CDISC Library comes along with an API, so this can be used by a program to load relevant data. Other library and dictionary providers might have an API where the data can be loaded from one system to another automatically. For the OpenStudyBuilder we have standard import programs in place which read the data from the CDISC API and stores the data in the database using the OpenStudyBuilder API - there are many parts in the API just responsible for standard imports.

On the right side we do have the OpenStudyBuilder application which is also only communicating with the database through the OpenStudyBuilder API. Other tools like a protocol tool (which is currently not open-sourced) access also all protocol information through the API. Any tool like also EDC tools can use the API to receive, send and update data.

The OpenStudyBuilder API is very powerful and contains a lot of data to receive and put. As other software which is made available to the pharmaceutical industry is not only designed for the OpenStudyBuilder, but should support also other environments from any pharma company. To overcome integration issues, the [TransCelerate DDF](https://www.transceleratebiopharmainc.com/initiatives/digital-data-flow/) project is working together with CDISC on API standards. The OpenStudyBuilder is working on a DDF-API-Adaptor which will be included in one of the next coming releases. This enables any software supporting the DDF-API standard to be also working with the OpenStudyBuilder.

![TransCelerate DDF API - Example](./img/guide_api_intro2.png)
{: class="imageParagraph"}

Figure 3: TransCelerate DDF API - Example
{: class="imageDescription"}

There could be a EDC tool supporting the DDF standards. By connecting just the different database, for example by specifying the URL in a configuration file, the original tool would not need any further integrations. Currently the DDF API might not be as powerful as required - for example the native API provides many additional features which are very valuable for EDC tools - but it is in development and throughout the years we are expecting the DDF API adaptor to contain all required functions.

## API and Execution

### OpenAPI and Swagger

For the API development and usage, there are excellent standards and tools available. The [OpenAPI](https://www.openapis.org/) is a very common format for API specifications. This specification which is available in the json format can be important into many API tools - for example into [Postman](https://www.postman.com/), a commonly used API tool. Additionally, there is the [Swagger](https://swagger.io/) documentation which allows also even execute API calls easily.

In the OpenStudyBuilder you can download the OpenAPI either from the [repository](https://gitlab.com/Novo-Nordisk/nn-public/openstudybuilder/OpenStudyBuilder-Solution/-/blob/main/clinical-mdr-api/openapi.json) directly, or you can click the link in the Swagger documentation top right. The Swagger documentation is an available component within the OpenStudyBuilder package - in the sandbox environment you can access this simply through a [URL](https://openstudybuilder.northeurope.cloudapp.azure.com/api/docs#/). In the other environments this is also available, for example by using a docker environment the URL is [http://localhost:5005/api/docs](http://localhost:5005/api/docs).

Remark **Sandbox Environment**: To get access to the Sandbox environment, you can simply send a mail to openstudybuilder@neotechnology.com with the subject "Request Sandbox Access". Your e-mail will be used together with Microsoft authentication to access the various tools via browser. Please be aware that your mail might be exposed when you perform changes as all changes are tracked for a version history. 

There are different operations you can do with an API. The following standard operations are typically used for tasks:

Operation | Description
--|--
GET | Retrieve data
PUT | Updates data
POST | Sends data for processing
DELETE | Removes data
PATCH | Updates data

### Swagger API Documentation

![Screenshot of Swagger API documentation (top section)](./img/guide_api_intro3.png)
{: class="imageParagraph"}

Figure 4: Swagger API documentation (top section)
{: class="imageDescription"}

The top section contains some general information including license information. Then there is an authentication section. If you have not changed the settings, the docker environment will have no authentication. But for the sandbox environment and most likely other environments, you do need to authenticate. You can simply click "authorize" and then in the pop-up again "authorize" to allow the API calls to be executed later on. Please note that the authentication is restricted by time, so you might have to click this again when automatically logged off.

By being authorized you cannot only see what API endpoints are available, but these can also be executed. There are many endpoints available which are grouped logically. Of course, it might be tricky to find the correct endpoint when you are not familiar with the used terminology used.

The ODM prefixes are for example connections related to ODM and CRF items. You can for example see CRF templates and download these in the ODM-XML format. The corresponding functionality in the app is located under "Library -> Concepts -> CRFs". The CT is all related to the controlled terminology management which is available in the application via "Library -> Code Lists".

### Swagger API Execution

To execute an API call within this website is very easy. After authentication we can search for "/studies" to get to the related calls. The short description gives a good overview of what call will do. 

![Screenshot of Swagger API documentation (Studies section)](./img/guide_api_execute1.png)
{: class="imageParagraph"}

Figure 5: Swagger API documentation (Studies section)
{: class="imageDescription"}

When the "Get /studies" section is enlarged, many options are available. You might want to restrict the resulting data, filter by various conditions. Below you see the structure of return values which you might receive on success or failure. We can click on "Try it out" to be able to fill out the different parameters and execute that API command.

!!! note

    Please note that the "filters" is pre-filled with an example `{"*":{ "v": [""], "op": "co"}}` - you need to remove this to get a result. This "filters" option is available and pre-filled in many calls, so please remember to remove those.

After executing this API call, you get a response.

![Screenshot of Swagger API Execution (/studies)](./img/guide_api_execute2.png)
{: class="imageParagraph"}

Figure 6: Swagger API Execution (/studies)
{: class="imageDescription"}

You receive a "Curl" statement, a "Request URL" and a "Response body". The "Response body" displays the data from your API call. The result is the "answer" to the API call question. It is available in JSON format, which is ideal to be processed further programmatically. The "CDISC DEV-0" study has for example the UID of "Study_000001". This is the unique identifier and is needed if you want to do follow up calls where you receive additional information or even change information.

The **"Request URL"** is nice to re-use in a browser or HTTP request. When using no authentication (for the docker environment for example), you can copy the URL into a browser and see the same result - just not formatted. If you want to use this HTTP request in any other tool like a web or R-Shiny application, you can simply use this URL. That's very generic and can be used from nearly any programming language. When you use authentication, e.g., like we have for the sandbox test environment, you need to take care for this and can work with that as well.

Most API tools support **CURL** requests. If you use a Linux system or a windows bash, you can even execute this CURL command to get the response. This CURL request also contains authentication (the bearer token in this case).

![Screenshot of Git Bash in Windows executing CURL command](./img/guide_api_execute3.png)
{: class="imageParagraph"}

Figure 7: CURL command executed in Git Bash in Windows
{: class="imageDescription"}

### R example

As mentioned, this API can be called in any other kind of software. Let's use as example an R application connecting the sandbox environment with authentication. There are different packages available for http and CURL requests. The following example is using the httr package.

```R

# CURL example to get API results from OpenStudyBuilder
#
# Remark - you can get the current bearer token by executing by calling the API from the browser and copy the token
#   goto - https://openstudybuilder.northeurope.cloudapp.azure.com/api/docs#/Studies/get_all_studies_get
#   click "authorize" top right lock symbol, then "authorize"
#   click "try it out"
#   remove everything from the "filters" field
#   click "execute"
#   copy the bearer token from the CURL command (long string after "-H 'Authorization: Bearer ")
#

# setup for sandbox environment
api_url <- "https://openstudybuilder.northeurope.cloudapp.azure.com/api"
api_bearer <- "...."    # get your specific one

library(httr)

response <- GET(paste(api_url,"studies", sep = "/"), add_headers(Authorization = paste("Bearer", api_bearer)))
studies <- jsonlite::fromJSON(rawToChar(response$content))
cat(studies[][["items"]][["uid"]], studies[][["items"]][["study_id"]])


response <- GET(paste(api_url,"ct/terms?codelist_name=Sex", sep = "/"), add_headers(Authorization = paste("Bearer", api_bearer)))
ct_sex <- jsonlite::fromJSON(rawToChar(response$content))
print(ct_sex[["items"]][["name"]][["sponsor_preferred_name"]])
```

We can simply get the resulting JSON file from a GET call and parse this into an R data frame. The first example ready in all studies which are available using the "/study" endpoint. Currently there is just one study available.

We can use also any other available endpoint. The second example shows how the "Sex" controlled terminology is downloaded.

Output:

```
> cat(studies[][["items"]][["uid"]], studies[][["items"]][["study_id"]])
Study_000001 CDISC DEV-0> 
> 
> print(ct_sex[["items"]][["name"]][["sponsor_preferred_name"]])
[1] "Female"   "Intersex" "Male"     "Unknown" 
```

![Screenshot of R data frame from API studies object](./img/guide_api_execute4.png)
{: class="imageParagraph"}

Figure 8: R data frame from API studies object
{: class="imageDescription"}