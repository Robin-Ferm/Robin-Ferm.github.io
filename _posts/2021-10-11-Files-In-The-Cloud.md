---
published: true
---
## What does the application do?

It locates and scans file from a folder and then uploads them to an Azure Blob Container, it gives you a few simple console messages related to the upload process and when it's complete along with the url for the picture.  

An image of what my console looks like when the process is complete.  
![image](https://user-images.githubusercontent.com/70013388/136730809-cc89f7bf-98f5-4fce-b6ba-7710d965a22e.png)  


An image of what my blob container looks like on the Azure portal.  
![image](https://user-images.githubusercontent.com/70013388/136730998-abf782d1-4431-4316-be91-808dfe283178.png)  

## Diagram describing dataflow 

Ugh.. I hate making these, i'll do it last.

## What does the code do?

First of all, I followed a pretty great youtube tutorial that you can see [here](https://youtu.be/JZWaWAU548g). He goes through pretty much everything I was to do in the assigment.

I started off with creating the method **GetConfiguration** which uses the **ConfigurationBulder class** and this method simply reads the connectionstring, container name and path to the folder with our images we want to upload. 

(insert picture of config file and method)  

And then I created the method **GetFiles** which takes one parameter that will be the path to the folder with the files we want to upload.

(insert picture of GetFiles method)  

The method **Upload**, like you might've guessed, uploads the files to our Azure blob storage. The method has three parameters which are the files that will be uploaded, the connectionstring and container name.
And then we create an instance of the BlobContainerClient class which allows us to manipulate the Azure storage container and its blobs. I use a foreach loop to iterate over every file that we upload and write out the appropriate message for each file.

(insert picture of Upload method)
