### [Cosmos DB](https://youtu.be/Jvgh64rvdXU)

Key Concepts:

- Account → top-level container of databases.
- Database → logical namespace inside an account.
- Container (Collection) → stores JSON documents.
- Partition key → distributes data across physical partitions.
- RU/s → Request Units per second, measure of throughput.

```
az login

az group create --name rg-free-weu-db --location westus

az cosmosdb create --name db-free-weu-cosmos --resource-group rg-free-weu-db --kind GlobalDocumentDB --locations regionName=westus failoverPriority=0 --enable-free-tier true --capabilities EnableServerless

az cosmosdb sql database create --account-name db-free-weu-cosmos --resource-group rg-free-weu-db --name aidb

az cosmosdb sql container create \
  --account-name db-free-weu-cosmos \
  --resource-group rg-free-weu-db \
  --database-name aidb \
  --name ai_rag_cnt \
  --partition-key-path "/id"
```

### Best Practices for Vector Search

- Use correct dimensions (match embedding model).
- Use quantizedFlat for efficiency.
- Keep vectors as float32 arrays.
- Use partition key wisely (/id is simplest).
- Monitor RU consumption → vector search can be RU-heavy.

### Additional Topics to Explore

- Change Feed → process data updates in real-time.
- Multi-region replication → low-latency global reads.
- Cosmos DB Emulator → local testing without cost.
- SDKs → Python, C#, Java, Node.js.
- Serverless vs Provisioned Throughput → cost optimization.
- Backup & Restore → data safety.

### IDE

- Cosmos DB account in Azure Portal -> Open Data Explorer from the left-hand menu.
- VS Code Extension: Azure Cosmos DB
