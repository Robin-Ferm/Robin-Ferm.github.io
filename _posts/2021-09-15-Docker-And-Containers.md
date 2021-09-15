---
published: true
---
## Docker and Containers

### Exercise 1: Hello World in Docker

I started with forking the _SimpleWebHalloWorld_ repository. I then created the Dockerfile using github, thereafter I opened my repository with Visual Studio Code where I Continued my work.

In Visual Studio Code I ran the command line _docker build -t simplewebhallowworld ._ to build the Docker Image, I then run the Docker Image using this command line: _docker run -d -p 8080:80  --name myapp simplewebhallowworld_

I had a lot of problem getting Docker to run my image, it kept saying it couldn't find .NET Core 3.1, and I had no idea why since I specified that we used .NET 5.0 but I finally figured out what the problem was and it was in the repository that we cloned, in the csproject file it said that we were using netcoreapp 3.1, when I changed that and saved, rebuilt and ran the image it all worked perfectly.



**Blog is being updated...**


References:

[Create a Dockerfile for an ASP.NET Core application](https://docs.docker.com/samples/dotnetcore/)
