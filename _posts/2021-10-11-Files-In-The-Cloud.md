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

Not the best diagram.. I'm terrible at these but I think this is how it all works.  

![image](https://user-images.githubusercontent.com/70013388/136736250-c2f6fbea-ca2c-45f8-8bae-05aa079ed9dd.png)

## What does the code do?

First of all, I followed a pretty great youtube tutorial that you can see [here](https://youtu.be/JZWaWAU548g). He goes through pretty much everything I was to do in the assigment.

I started off with creating the method **GetConfiguration** which uses the **ConfigurationBulder class** and this method simply reads the connectionstring, container name and path to the folder with our images we want to upload. 

Config file.  
![image](https://user-images.githubusercontent.com/70013388/136733061-7eecf0d2-ed34-4040-aa4b-dde1eb1adf59.png)  

GetConfiguration Method  
![image](https://user-images.githubusercontent.com/70013388/136733093-338cfb01-8fff-480a-95e1-f2c02cdcfb83.png)


And then I created the method **GetFiles** which takes one parameter that will be the path to the folder with the files we want to upload.  

GetFiles Method.  
![image](https://user-images.githubusercontent.com/70013388/136733160-e7362f6d-ca13-41ac-aab8-048477cd2db2.png)  

The method **Upload**, like you might've guessed, uploads the files to our Azure blob storage. The method has three parameters which are the files that will be uploaded, the connectionstring and container name.
And then we create an instance of the BlobContainerClient class which allows us to manipulate the Azure storage container and its blobs. I use a foreach loop to iterate over every file that we upload and write out the appropriate message for each file.

![image](https://user-images.githubusercontent.com/70013388/136733383-9fd86687-39eb-4c30-9273-74463cda524b.png)  

This is what our main method looks like when everything is done.  
![image](https://user-images.githubusercontent.com/70013388/136733449-2f9edbba-7bdf-459d-b628-dfe725324a8a.png)  

## What would the cost of the application be?

If our program was used by 1000 users who each upload 100MB each day we would need 36500GB of storage for exactly one year. So my pricing calculations are based on one ears worth of storage. Just for that storage the cost would be around $803. I'm not sure how much it would cost if we had our users download all the pictures three times per day since Azures Caluclator keeps telling me it's $0, but it max out at 5000GB, the price doesn't change so I have no idea how much that would cost.

## How does Microsoft secure our blob data?

Microsoft is kind enough (well, maybe not kind, I guess it would be a pretty shitty PR storm if they had a data breach and nothing was encrypted) to encrypt all the data on your Azure Blob that you've uploaded to a disk and then they decrypt i t whenever you want to access it. And to prevent the data to be intercepted when data is being transferred over the open internet to and from the cloud storage they alos encrypt all the data using the **Transport Layer Security protocol** and **Forward Secrecy**.
