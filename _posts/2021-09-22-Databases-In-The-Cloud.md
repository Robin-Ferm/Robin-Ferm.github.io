---
published: true
---
## What does the application do?

Well, it's a very simple application, I had  some problems get it to work so I decided to make it as simple as possible. The only thing it does is it takes two strings and adds it to a Cosmos Database. It stores names of movies and if you've watched them or not. Also, when I found [these](https://docs.microsoft.com/sv-se/azure/azure-functions/functions-add-output-binding-cosmos-db-vs-code?pivots=programming-language-csharp) documentations on the Microsoft page everything got a lot more smoother. I'd probably be stuck forever if I hand't stumbled upon them.

![image](https://user-images.githubusercontent.com/70013388/135697623-dd7353f8-b024-476d-b33c-44b724f9de2e.png)

Here is my POST method.
![image](https://user-images.githubusercontent.com/70013388/135697644-0c7418ed-f5ec-4458-8938-5c65afde6b82.png)  

You can see I'm not using my MovieModels class and that's simply because I didn't need to.. I didn't know I needed one when writing this code, and it all works like it should. You can only input two strings and if you decide to not input the second string it'll just be null. But I had to add the MovieModels class in my GET method since I couldn't get that to work, so that was the only solution I found to get it to return my database, along with a query where I select everything in the database and return it.


Here is my GET method. There are no try and catches in either of them for now, I'm a little late with the assignment so I'll just get this done for now.  

![image](https://user-images.githubusercontent.com/70013388/135697663-c83a7ea3-9d76-4359-b752-ecfff09b2b52.png)

Here is my MovieModels Class  

![image](https://user-images.githubusercontent.com/70013388/135697703-b022ad00-33a1-4809-9324-90ebc2a5f215.png)  


Here you can see me using Postman to POST a movie into the database.  

![image](https://user-images.githubusercontent.com/70013388/135697792-31f0f148-fdf5-4a88-91a6-2ce55aa79670.png)

Here is a picture of my CosmosDB item list. Don't mind the name ToDoList, I scrapped that project when I got stuck so I changed it to a movie database instead just to keep things simple.  

![image](https://user-images.githubusercontent.com/70013388/135697813-005799c4-0b53-4998-a2a2-45b5ec7556cd.png)


## How did I get it to run in Azure Functions?

Well, creating the Cosmos Database was pretty simple when I followed [this tutorial](https://youtu.be/R_Fi59j6BMo)  
However, I did run into a problem when I published my function to the cloud, it is up and running but I'm having trouble accessing it, I get a 401 error which I think has something to do with my API key. And yet again I got stuck here so what you're seeing up above is screenshots from localhost.
I published the function using Visual Studio Code with the help of the Azure extention.


- Hur har du tänkt runt uppdatring av databsen ifall scheman ändras? Migrations?

## Have I a plan for updating and expanding the databse?

Not really, when I built the application I didn't plan for it to even be able to grow, I was just focused on it to work the way I wanted it to. 

## What would it cost to run this?  

well, if it's just a few users it would probably be free since there won't be many requests at all, making maybe a handful of requests each week. But if the userbase would grow it could be a lot more expensive I think, especially if their movielists were really big then the querying would take more and more RU/s.  

An Azure Cosmos DB with the lowest amount of RU/S would cost $23.36 and a function with one million executions per month is $0 so.. pretty cheap. If we scale it up it obviously costs a lot more.

References

[Azure Functions and Cosmos DB Microsoft Docs](https://docs.microsoft.com/sv-se/azure/azure-functions/functions-add-output-binding-cosmos-db-vs-code?pivots=programming-language-csharp)





