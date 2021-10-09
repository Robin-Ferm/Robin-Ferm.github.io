---
published: true
---
## What does the application do?

well, it's quite simple actually. It's a To do list website! You input things into a list that you're planning on doing, and you can edit the things already in the database or you can delete them.  

![image](https://user-images.githubusercontent.com/70013388/136637054-1da24e02-c15e-46d6-a4d6-f725ba1598f2.png)  


I gave up  on my movielist project, which was my database from the previous lecture. I couldn't get it to work properly, only managed to display the things I've already put in the databse, so I instead tried to look for a tutorial on how to do this properly, which led me to the To-do list! I followed [this tutorial](https://docs.microsoft.com/en-us/azure/cosmos-db/sql/sql-api-dotnet-application) mostly.  

## What does to code do?  

A lot of the code is from the template when creating an ASP.NET Core Web App but I'll try to explain how it works.  

Class  
![image](https://user-images.githubusercontent.com/70013388/136636491-b7649955-7075-4304-88e6-c6b80a1574d4.png)  


And then there is the CosmosDbService class that I added which contains all the logic for us to connect to and use the Azure Cosmos DB. This service does the CRUD operations.  


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

I also created an interface called ICosmosDbService.  
 
![image](https://user-images.githubusercontent.com/70013388/136636862-21cbb89b-5cae-4328-bce7-5b658f180604.png)  


Then I had to add the following method  InitializeCosmosClientInstanceAsync ino the Startup.cs file, this method then reads the configuration and initializes the client.  

![image](https://user-images.githubusercontent.com/70013388/136636929-5fae0b83-f3b8-43f0-8717-19f30f5e53f3.png)  

And like the previous project where we created our CosmosDB I had to add the appropriate values for the Primary Key and the Endpoint URI.  
