---
published: true
---
## Docker and Containers

### Exercise 1: Hello World in Docker


I started with forking the _SimpleWebHalloWorld_ repository. I then created the Dockerfile using github, thereafter I opened my repository with Visual Studio Code where I Continued my work.

My docker file with comments explaining each section.
![image](https://user-images.githubusercontent.com/70013388/133518834-2120f18e-bc53-441b-9fa2-d6e08560c02e.png)<br/><br/><br/>


In Visual Studio Code I ran the command line _docker build -t simplewebhalloworld ._ to build the Docker Image, I then run the Docker Image using this command line: _docker run -d -p 8080:80  --name helloworld simplewebhalloworld_

I had a lot of problem getting Docker to run my image, it kept saying it couldn't find .NET Core 3.1, and I had no idea why since I specified that we used .NET 5.0 but I finally figured out what the problem was and it was in the repository that we cloned, in the csproject file it said that we were using netcoreapp 3.1, when I changed that and saved, rebuilt and ran the image it all worked perfectly.

An image of the line I had to change to 5.0 from 3.1 to get it to work properly
![image](https://user-images.githubusercontent.com/70013388/133517861-833a0f59-300c-4eb4-9cfd-9ba04456f5fc.png)<br/><br/><br/>


## My github pipeline

When creating my pipeline I first had to create a yml file with the following content which you can see here:

![image](https://user-images.githubusercontent.com/70013388/133529664-94c37685-36d4-47a9-9ddc-2d1c3e426c61.png)<br/><br/><br/>

The pipeline activates when a push is made to the master branch. What happens is that the pipeline builds a docker image which then logs in to the github container registry (ghcr). Here we use our github username and our personal access token that we've created to see if everything matches up, which (finally) it does.
Our image is now finally pushed to my github account, I didn't really know how to make it so it was connected to the repository automatically but it was easy enough to manually attach it to our repository, which I did.

Here we can see that the workflow executed and finished without any errors.

![image](https://user-images.githubusercontent.com/70013388/133531062-b2bf88c7-7982-4e06-a39c-b2d5cba55cab.png)<br/><br/><br/>


We can also see here that our image was uploaded and is now linked to our repository.

![image](https://user-images.githubusercontent.com/70013388/133531186-fd46faaa-1ede-4617-8460-0b50fd1b0ace.png)<br/><br/><br/>

[Here is a link to the repository.](https://github.com/Robin-Ferm/SimpleWebHalloWorld)

How did I create a Personal Access Token?
Well, all I had to do was go into **Settings > Developer Settings > Personal access tokens** and there I just created a new token, and then I went into our repository again, went to **Settings > Secrets** and there I added the token I got before and created a name for it, in this case the name was SECRET_PAT which has to be the exakt name you use in your yml file later or the build will fail, I'm speaking from experience here, but trial and error fixed it and now it all works like it should.<br/><br/>


**Programs I used was:**

**Docker Desktop**  
**Visual Studio Code**  
**Github**  <br/>

## References:

[Create a Dockerfile for an ASP.NET Core application](https://docs.docker.com/samples/dotnetcore/)

[Creating a personal access token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token)
