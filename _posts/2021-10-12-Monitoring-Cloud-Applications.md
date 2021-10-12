---
published: true
---
## What does the application do?  

Well, the application does what it did in lecture 6, it's a To-Do list, but this time around it also logs everytging that is happening.

## Diagram  

(insert boring diagram here)

## What does the code do?  

ConfigureLogger Method

![image](https://user-images.githubusercontent.com/70013388/136940756-fcbebc52-c807-4967-b821-fae1505d304d.png)  

I created a static method that will overwrite the default logging.

Main Method  

![image](https://user-images.githubusercontent.com/70013388/136940830-6c0bb3f0-c831-4e88-8837-dbf099cf9736.png)  

In the Main Method we call our ConfigureLogger Method to run on startup. We also log a simple message showing that we've started the program.


Simple example of how I added a message when CreateAsync() is called.

![image](https://user-images.githubusercontent.com/70013388/136941597-0c7b14f7-0077-497d-a0e0-1f9a677dfb72.png)



## Describe how logging can help you with security in your application  

## Explain your queries

This query shows how many requests is from a specific city on a specific day.  

![image](https://user-images.githubusercontent.com/70013388/136937784-2e16e7f8-c921-4728-b0ca-3f4fe49871d3.png)  

This query shows all messages with the string "ITEM DELETED" on the specified day.  

![image](https://user-images.githubusercontent.com/70013388/136940020-2c4d30f0-99ea-479e-aff8-a66acf2a9c3e.png)



### References  

[How to integrate Serilog in .Net Core Application](https://youtu.be/7YuBYEfqcvI)
