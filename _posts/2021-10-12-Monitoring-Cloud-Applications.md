---
published: true
---
## What does the application do?  

Well, the application does what it did in lecture 6, it's a To-Do list, but this time around it also logs everything that is happening via our Application Insight on Azure.
There wasn't much code needed to get it to run really, a few simple lines here and there. I guess I could've done more with it but im behind schedule so I'm just trying to get it to work properly.  


## What does the code do?  

ConfigureLogger Method

![image](https://user-images.githubusercontent.com/70013388/136940756-fcbebc52-c807-4967-b821-fae1505d304d.png)  

I created a static method that will overwrite the default logging. And here we tell Serilog where to write our logs, and in this case it is to our ApplicationInsight on Azure.
I decided no to write to the console or a file in this case.

Main Method  

![image](https://user-images.githubusercontent.com/70013388/136940830-6c0bb3f0-c831-4e88-8837-dbf099cf9736.png)  

In the Main Method we call our ConfigureLogger Method to run on startup. We also log a simple message showing that we've started the program.


Simple example of how I added a message when CreateAsync() is called.

![image](https://user-images.githubusercontent.com/70013388/136941597-0c7b14f7-0077-497d-a0e0-1f9a677dfb72.png)

I added UseSerilog() here  

![image](https://user-images.githubusercontent.com/70013388/136943028-c3a0154e-a108-470e-b6b7-097b3331e077.png)



## Describe how logging can help you with security in your application  

There are many security benefits of logging, for example, Azure offers a way for you to get alerts with your own alert rules that you've set with different conditions.
Logging user actions can also help you improve your security in lots of ways because it provides a way for the administrators to reconstruct events, detect intrusions and analyze problems such a s poor performance or unexpected system behavior. 


## Explain your queries

This query shows how many requests is from a specific city on a specific day.  

![image](https://user-images.githubusercontent.com/70013388/136937784-2e16e7f8-c921-4728-b0ca-3f4fe49871d3.png)  

This query shows all messages with the string "ITEM DELETED" on the specified day.  

![image](https://user-images.githubusercontent.com/70013388/136940020-2c4d30f0-99ea-479e-aff8-a66acf2a9c3e.png)



### References  

[How to integrate Serilog in .Net Core Application](https://youtu.be/7YuBYEfqcvI)
