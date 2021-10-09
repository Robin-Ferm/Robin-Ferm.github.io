---
published: true
---
## What does the application do?

well, it's quite simple actually. It's a To do list website! You input things into a list that you're planning on doing, and you can edit the things already in the database or you can delete them.
I gave up  on my movielist project, which was my database from the previous lecture. I couldn't get it to work properly, only managed to display the things I've already put in the databse, so I instead tried to look for a tutorial on how to do this properly, which led me to the To-do list! I followed [this tutorial](https://docs.microsoft.com/en-us/azure/cosmos-db/sql/sql-api-dotnet-application) mostly.

## What does to code do?

A lot of the code is from the template when creating an ASP.NET Core Web App but I'll try to explain how it works.

Class
![image](https://user-images.githubusercontent.com/70013388/136636491-b7649955-7075-4304-88e6-c6b80a1574d4.png)


And then there is the CosmosDbService class that I added which contains all the logic for us to connect to and use the Azure Cosmos DB. This service does the CRUD operations.
I also created an interface called ICosmosDbService.

```
public class CosmosDbService : ICosmosDbService
    {
        private Container _container;

        public CosmosDbService(
            CosmosClient dbClient,
            string databaseName,
            string containerName)
        {
            this._container = dbClient.GetContainer(databaseName, containerName);
        }

        public async Task AddItemAsync(Item item)
        {
            await this._container.CreateItemAsync<Item>(item, new PartitionKey(item.Id));
        }

        public async Task DeleteItemAsync(string id)
        {
            await this._container.DeleteItemAsync<Item>(id, new PartitionKey(id));
        }

        public async Task<Item> GetItemAsync(string id)
        {
            try
            {
                ItemResponse<Item> response = await this._container.ReadItemAsync<Item>(id, new PartitionKey(id));
                return response.Resource;
            }
            catch (CosmosException ex) when (ex.StatusCode == System.Net.HttpStatusCode.NotFound)
            {
                return null;
            }

        }

        public async Task<IEnumerable<Item>> GetItemsAsync(string queryString)
        {
            var query = this._container.GetItemQueryIterator<Item>(new QueryDefinition(queryString));
            List<Item> results = new List<Item>();
            while (query.HasMoreResults)
            {
                var response = await query.ReadNextAsync();

                results.AddRange(response.ToList());
            }

            return results;
        }

        public async Task UpdateItemAsync(string id, Item item)
        {
            await this._container.UpsertItemAsync<Item>(item, new PartitionKey(id));
        }
    }
```
