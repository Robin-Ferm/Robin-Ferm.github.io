---
published: true
---
## Docker and Containers

### Exercise 1: Hello World in Docker

I started with forking the _SimpleWebHalloWorld_ repository. I then created the Dockerfile using github, thereafter I opened my repository with Visual Studio Code where I Continued my work.

My docker file with comments explaining each section.
![image](https://user-images.githubusercontent.com/70013388/133518834-2120f18e-bc53-441b-9fa2-d6e08560c02e.png)


In Visual Studio Code I ran the command line _docker build -t simplewebhalloworld ._ to build the Docker Image, I then run the Docker Image using this command line: _docker run -d -p 8080:80  --name helloworld simplewebhalloworld_

I had a lot of problem getting Docker to run my image, it kept saying it couldn't find .NET Core 3.1, and I had no idea why since I specified that we used .NET 5.0 but I finally figured out what the problem was and it was in the repository that we cloned, in the csproject file it said that we were using netcoreapp 3.1, when I changed that and saved, rebuilt and ran the image it all worked perfectly.

An image of the line I had to change to 5.0 from 3.1 to get it to work properly
![image](https://user-images.githubusercontent.com/70013388/133517861-833a0f59-300c-4eb4-9cfd-9ba04456f5fc.png)  


## My github pipeline

When creating my pipeline I first had to create a

![image](https://user-images.githubusercontent.com/70013388/133529664-94c37685-36d4-47a9-9ddc-2d1c3e426c61.png)


**Blog is being updated...**


References:

[Create a Dockerfile for an ASP.NET Core application](https://docs.docker.com/samples/dotnetcore/)
