---
published: true
---
## What does the application do?

well, it's quite simple actually. It's a To do list website! You input things into a list that you're planning on doing, and you can edit the things already in the database or you can delete them.  

![image](https://user-images.githubusercontent.com/70013388/136637054-1da24e02-c15e-46d6-a4d6-f725ba1598f2.png)  


I gave up  on my movielist project, which was my database from the previous lecture. I couldn't get it to work properly, only managed to display the things I've already put in the databse, so I instead tried to look for a tutorial on how to do this properly, which led me to the To-do list! I followed [this tutorial](https://docs.microsoft.com/en-us/azure/cosmos-db/sql/sql-api-dotnet-application) mostly.  

## What does to code do?  

A lot of the code is from the template when creating an ASP.NET Core Web App but I'll try to explain how it works.  

Here is our model class called Item, not much to explain really.  

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

And like the previous project where we created our CosmosDB I had to add the appropriate values for the Primary Key and the Endpoint URI to the appsettings.json file  

And here is a picture from my Azure Portal to show you the items we have in our container.  

![image](https://user-images.githubusercontent.com/70013388/136637297-c17422a0-97ad-46dd-9bfe-66f4b3a6196c.png)

## How did I get it to run on Azure?

Well, that was extremely simple aswell. Right click your poject in your solution explorer and select Publish, it will then guide you through the process of publishing your project to Azure. It was pretty straight forward, just make sure you're logged into your Azure account. I used Visual Studio and not Visual Studio Code to publish this app.  


## What would it cost to run this application?

For the cheapest App Service I'd have to spend $54.7 a month. For this simple application that doesn't have much use I'd say that's not really worth it, but 50 bucks a month for something like this isn't too bad either. Adding a CosmosDB with 10gb of Transactional Storage adds another $25 which would mean this whole project would cost something like $80



