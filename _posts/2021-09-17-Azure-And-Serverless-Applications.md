---
published: true
---
## What Is Serverless And Function As A Service?


The short and simple answer would be that **Serverless** is a cloud-native development model that allows developers to build an run applications without having to manage servers themselves. The name serverless might make you believe there are no servers at all but thats not true, there are still servers but they are managed by the cloud provider so you don't have to think about it at all, you can instead focus on your application.

**Function as a Service** (FaaS) means you write and deploy standalone functions on the cloud, instead of entire apps. Each function serves a distinct need and handles a distinct event, like a web request.

The functions you write are only loaded in memory when there is a request or event for them to handle and unloaded after serving that request. They also share the same hardware and possibly the same runtime with everybody else’s functions. As a result, you generally only pay for the CPU time consumed by your functions, and not for the entire server or VM.

In the picture below you can see my code for the HTTP trigger, most of the code comes from the template, the only lines I added were a few more strings from line 13 to 15 and then again at line 22 to 24 and after that it was a simple if statement to do the calculations depending on the input which I in this case called math for some reason. And at line 49 I added a little message and our values and sum which will be shown when the trigger is run.

![image](https://user-images.githubusercontent.com/70013388/133864914-c6f778c1-5764-46f2-adcc-81b884cdb953.png)


And here you can see our response code and the response message.

![image](https://user-images.githubusercontent.com/70013388/133864390-1816eda6-70ae-40bd-ac4a-cfd99235f40c.png)


### How have I tested my application?

I made the application in both the Azure web interface and with Visual Studio but I couldn't get it to work properly with Visual Studio so I copy pasted everything into the Azure Web Interface when I was done coding and ran it there and did my tests. All the basic math stuff works, we get 500 Internal Server Error if we input letters instead of numbers.

### How did I get my application up and running?

It was actually pretty simple, I logged into the [Azure Portal](https://portal.azure.com/#home)

### Are there any security risks with my application?
Honestly.. I don't really know, since it's such a small application I'm having a hard time figuring out if there is any risk at all, there is literally no data to find anywhere, nothing is stored, no database connected. Maybe someone can spam the program with multiple requests which would shut it down or something?





References

[What is Serverless?](https://quanticdev.com/articles/serverless/)
