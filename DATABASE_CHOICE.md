# Database Choice

## Your Choice

I selected **Azure Cosmos DB using the NoSQL API** for storing the Text Analyzer results.

## Justification

Azure Cosmos DB is the best choice for this use case because the Text Analyzer results are already structured as JSON documents. It allows each analysis result to be stored without creating a fixed relational schema. Cosmos DB also works well with Azure Functions and supports serverless pricing, which is suitable for a student lab project. Since the project includes a history endpoint, Cosmos DB makes it easy to store and retrieve previous analysis records.

## Alternatives Considered

### Azure Table Storage

Azure Table Storage is a low-cost NoSQL option, but it is better suited for simple key-value or table-style data. It is less flexible for storing nested JSON analysis results compared to Cosmos DB.

### Azure SQL Database

Azure SQL Database is powerful for relational data, structured tables, joins, and transactions. However, this project does not require complex relationships or a fixed schema, so SQL would add unnecessary complexity.

### Azure Blob Storage

Azure Blob Storage can store JSON files, but it is not a true database. It would be harder to query and retrieve individual analysis records efficiently, especially for the history endpoint.

## Cost Considerations

Azure Cosmos DB offers serverless pricing, where costs are based on the number of request units used by database operations. This is suitable for a small serverless application because there is no need to provision dedicated database capacity. For a student lab with low usage, the cost should remain minimal, especially compared to always-on database options.