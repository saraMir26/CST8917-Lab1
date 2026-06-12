# CST8917 Lab 1 – Azure Functions Text Analyzer with Cosmos DB

## Overview

This project demonstrates the development and deployment of a serverless application using Azure Functions and Azure Cosmos DB.

The application provides two HTTP-triggered endpoints:

1. **TextAnalyzer** – Analyzes submitted text and generates statistics such as word count, sentence count, character count, reading time, and more.
2. **GetAnalysisHistory** – Retrieves previously stored analysis results from Azure Cosmos DB.

All analysis results are stored in Azure Cosmos DB and can be retrieved through the history endpoint.

---

## Technologies Used

* Python 3.12
* Azure Functions
* Azure Functions Core Tools
* Azure Cosmos DB (NoSQL API)
* Visual Studio Code
* Azure Portal

---

## Project Structure

```text
.
├── function_app.py
├── requirements.txt
├── local.settings.json
├── host.json
├── DATABASE_CHOICE.md
├── README.md
└── DEMO.md
```

---

## Required Environment Variables

Create a `local.settings.json` file for local development and configure the following values:

```json
{
  "IsEncrypted": false,
  "Values": {
    "FUNCTIONS_WORKER_RUNTIME": "python",
    "AzureWebJobsStorage": "UseDevelopmentStorage=true",
    "COSMOS_ENDPOINT": "<cosmos-endpoint>",
    "COSMOS_KEY": "<cosmos-key>",
    "COSMOS_DATABASE_NAME": "TextAnalyzerDB",
    "COSMOS_CONTAINER_NAME": "AnalysisResults"
  }
}
```

---

## Running the Application Locally

Start Azurite:

```bash
Azurite: Start
```

Start the Azure Function:

```bash
func start
```

---

## API Endpoints

### Text Analyzer

**GET**

```text
http://localhost:7071/api/TextAnalyzer?text=Serverless computing is amazing.
```

**POST**

```http
POST http://localhost:7071/api/TextAnalyzer
Content-Type: application/json

{
  "text": "Serverless computing is amazing."
}
```

### Get Analysis History

Retrieve previously stored analysis records:

```text
http://localhost:7071/api/GetAnalysisHistory
```

Retrieve a limited number of records:

```text
http://localhost:7071/api/GetAnalysisHistory?limit=5
```

---

## Azure Cosmos DB Configuration

Database:

```text
TextAnalyzerDB
```

Container:

```text
AnalysisResults
```

Partition Key:

```text
/id
```

---

## Deployment

The Azure Function App was deployed to Azure using Visual Studio Code Azure Functions Extension.

After deployment, the Cosmos DB connection settings were configured through Azure Function App Environment Variables.

---

## Demo Video

Video Link:

[![Watch the demo](https://img.youtube.com/vi/3kXiuihoT14/hqdefault.jpg)](https://www.youtube.com/watch?v=3kXiuihoT14)

---

## Author

Sara Mirzaei

CST8917 – Serverless Applications

