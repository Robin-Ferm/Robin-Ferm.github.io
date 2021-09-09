---
published: true
---
## What is CI/CD Pipeline?

CI/CD stands for **C**ontinuous **i**ntegration/**c**ontinuous **d**elivery and is a series of steps that must be performed in order to deliver a new version software.
These steps can be different for your organization but a very common series of step would look something like this.
- Build
	The stage where the application is compiled.
- Test
 	The stage where code is tested. Automation here can save both time and effort.
- Release
	The stage where the application is delivered to the repository.
- Deply
	 In this stage code is deployed to production.
- Validation and compliance
	The steps to validate a build are determined by the needs of your organization. Image security scanning 	tools, like Clair, can ensure the quality of images by comparing them to known vulnerabilities (CVEs).
    
      


**Tl;dr** CI is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early.


## How I Created My CL Pipeline

Well, first of all I read and watched some tutorials which I'll link at the bottom of the page. I hade literally no idea how or what to do and I still don't really understand what I'm doing.
But essentially all I did was go into github, fork an older project called SpacePark v1 and then went into the Actions tab and there they had different templates to chose from so I picked .NET since thats what we used to develop our program with. And it basically gave me 99% of all the things that I needed (as far as I know). 

At first it didn't work properly, it coulnd't find the solution file but I found a solution to that problem which was to add _'working-directory: Source'_ to line 18 and 21, and this would then locate the solution file that it needed. However, the tests doesn't go through since the actual tests are stored in a SQL database which was part of the assignment in the SpacePark project. Not really sure how to solve that one..
But other than that I think it works.

![cii.png]({{site.baseurl}}/_posts/cii.png)


However, the tests doesn't go through since the actual tests are stored on a SQL database which was part of the assignment in the SpacePark project. Not really sure how to solve that one..
But other than that I think it works.


![failed.png]({{site.baseurl}}/_posts/failed.png)


  
**References used:**

[What is a CI/CD pipeline?](https://www.redhat.com/en/topics/devops/what-cicd-pipeline)

[Understanding the CI/CD Pipeline](https://www.plutora.com/blog/understanding-ci-cd-pipeline)

[Understanding Github Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)

[C# ASP.NET CI/CD With Github Actions](https://youtu.be/R5ppadIsGbA)
