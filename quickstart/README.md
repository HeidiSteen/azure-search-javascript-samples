---
page_type: sample
languages:
  - javascript
  - typescript
  - nodejs
name: JavaScript quickstart for Azure AI Search
description: |
  Learn how to create, load, and query an Azure AI Search index using the Azure SDK for Javascript/Typescript.
products:
  - azure
  - azure-cognitive-search
urlFragment: javascript-quickstart
---

# JavaScript quickstart for Azure AI Search

![Quickstart sample MIT license badge](https://img.shields.io/badge/license-MIT-green.svg)

Demonstrates using JavaScript and the [Azure SDK for JavaScript/TypeScript](https://learn.microsoft.com/javascript/api/overview/azure/search-documents-readme?view=azure-node-latest) to create an Azure AI Search index, load it with documents, and execute a few queries. The index is modeled on a subset of the Hotels dataset, reduced for readability and comprehension. Index definition and documents are included in the code.

This Node.js console application is featured in [Quickstart: Create an Azure AI Search index using the JavaScript SDK](https://learn.microsoft.com/azure/search/search-get-started-javascript). When you run the program, a console window emits output messages for each step: deleting and then re-creating a hotels-quickstart index, loading documents, running queries. This sample uses the [Azure SDK for JavaScript/TypeScript](https://learn.microsoft.com/javascript/api/overview/azure/search-documents-readme?view=azure-node-latest) and runs on a search service using connection information that you provide.

## Prerequisites

+ [Node.js](https://nodejs.org).
+ [NPM](https://www.npmjs.com) should be installed by Node.js.
+ [Create a search service in the portal](search-create-service-portal.md) or [find an existing service](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Search%2FsearchServices) under your current subscription. You can use a free service for this quickstart.
+ [Visual Studio Code](https://code.visualstudio.com) or another IDE.

## Set up the sample

1. Clone or download this sample repository.

1. Open the folder in Visual Studio Code and navigate to the quickstart folder:

   ```cmd
   cd quickstart
   ```

1. Install the dependencies using `npm`:

    ```bash
    npm install
    ```

1. Edit the file `sample.env`, adding the connection information that's valid for your Azure AI Search service. See 

   ```nodejs
   SEARCH_API_KEY=<search-admin-key>
   SEARCH_API_ENDPOINT=https://<search-service-name>.search.windows.net
   ```

1. Rename `sample.env` to just `.env`. The quickstart will read the `.env` file automatically.

## Run the sample

1. Run the following command to start the program.

    ```bash
    node index.js
    ```

You should see a series of messages relating to the creation of the search index, adding documents to it, and, finally, results of a series of queries.

If you get a 401 error, make sure the API key is correct (you need an admin API key to create objects), and make sure the search service is configured for [key-based authentication](https://learn.microsoft.com/azure/search/search-security-api-keys).

## Key concepts

The file **hotels_quickstart_index.json** holds the definition of an index for the data in the file **hotels.json**. Review those files to see the fields, which ones are searchable, etc.

The file **index.js** automatically reads the **.env** file which contains the  `SEARCH_API_KEY` and `SEARCH_API_ENDPOINT` needed to create the `SearchIndexClient`. The `sleep` function is used to pause execution in between major steps such as creating the index, submitting data for indexing, etc. Such pauses are generally only needed in test, demo, and sample code.

The `run` function :

+ Checks if the `hotels-quickstart` index exists.
+ If so, the program deletes the existing index.
+ Creates a new `hotels-quickstart` index from the structure in **hotels_quickstart_index.json**.
+ Adds the data from **hotels.json** to the `hotels-quickstart` index.
+ Executes a few basic queries against the search index.

## Next steps

You can learn more about Azure AI Search on the [official documentation site](https://learn.microsoft.com/azure/search/).

You can view additional samples for JavaScript/TypeScript in the [azure-sdk-for-js repo](https://github.com/Azure/azure-sdk-for-js/tree/master/sdk/search/search-documents/samples) or see the [documentation](https://learn.microsoft.com/javascript/api/overview/azure/search-documents-readme?view=azure-node-latest).
