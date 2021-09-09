---
published: false
---
# What is CI/CD Pipeline?

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


**References used:**

[What is a CI/CD pipeline?](https://www.redhat.com/en/topics/devops/what-cicd-pipeline)
[Understanding the CI/CD Pipeline](https://www.plutora.com/blog/understanding-ci-cd-pipeline)
