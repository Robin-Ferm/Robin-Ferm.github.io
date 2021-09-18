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




**Blog is currently being updated and written...**





References

[What is Serverless?](https://quanticdev.com/articles/serverless/)
