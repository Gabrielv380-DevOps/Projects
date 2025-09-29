<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Connect a GitHub Repo with AWS

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-github)

**Author:** Kenmore Valentine Sandoval  
**Email:** gabrielv380@gmail.com

---

## Connect a GitHub Repo with AWS

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-github_dd9d254e)

---

## Introducing Today's Project!

Today I am will be setting up a Git repository for my web app's code. This is project TWO in My 7 day DevOps challenge. By the end of this project, the code that I write for my Java web app will be stored securely in GitHub.

### Key tools and concepts

 Key concepts I learnt include how to deploy a Java web application using several key AWS services and DevOps concepts. You worked with Amazon EC2 to host and develop your application in the cloud, and used Visual Studio Code as your IDE, connected directly to your EC2 instance for seamless remote development. You also used GitHub for version control and code management.

On the CI/CD side, you explored the roles of AWS CodeArtifact for managing dependencies, AWS CodeBuild for automating the build and test process, AWS CodeDeploy for handling deployments across EC2 instances, and AWS CodePipeline to integrate all these steps into a streamlined, automated workflow. These services together taught you how to automate software delivery, improve deployment reliability, and reduce manual effort, core principles of modern DevOps.

### Project reflection

This project took me approximately 2 hours. It was most rewarding to connect my Git Repository and add my README file and allowing updates to be automatically pushed through Git.

I did this project today to gain hands-on experience with deploying a Java web application using AWS cloud services and to deepen my understanding of DevOps practices. By working through the setup and integrating CI/CD tools like CodeBuild, CodeDeploy, and CodePipeline, I was able to explore how automation can streamline software delivery and improve reliability. This project also helped me practice cloud-based development using EC2 and remote coding with Visual Studio Code, while reinforcing version control skills through GitHub. Overall, it was a practical step toward mastering cloud-native development and continuous deployment workflows.

This project is part two of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tomorrow.

---

## Git and GitHub

Git is like a time machine and filing system for your code. It tracks every change you make, which lets you go back to an earlier version of your work if something breaks. You can also see who made specific changes and when they were made, which makes teamwork/collaboration a lot easier. I installed Git using the commands "sudo dnf install git -y".

GitHub is a cloud-based platform that hosts Git repositories, making it easy to manage and collaborate on code. It provides tools for version control, issue tracking, and team collaboration, which are essential for modern software development. By using GitHub, I can store my code securely online, track changes over time, and work with others on shared projects. It also integrates seamlessly with tools like VSCode and AWS, allowing me to push and pull code between my local machine, EC2 instance, and GitHub repository with ease. This setup helps streamline my workflow and ensures that my code is backed up and accessible from anywhere.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-github_efaadbf7)

---

## My local repository

A Git repository is used to store your code using Git. You create repositories (aka 'repos'), which are folders that contain all your project files and their entire version history. Hosting a repo in the cloud, like on GitHub, means you can also collaborate with other engineers and access your work from anywhere.

When you run git init inside a directory e.g. nextwork-web-project, it sets up the directory as a local Git repository, which means changes are now tracked for version control.

A branch in Git is like a separate workspace or timeline within your project where you can make changes without affecting the main codebase. It allows me to work on new features, bug fixes, or experiments independently. When I'm ready, I can merge the branch back into the main branch (usually called main or master), combining the changes safely.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-github_7bf21bae)

---

## To push local changes to GitHub, I ran three commands

### git add

The first command I ran was "git add". When you stage changes, you're telling Git to put together all your modified files for a final review before you commit them. This is incredibly handy because you get to see all your edits in one spot, which means its much easier to check if there were are mistakes or unwanted changes before you commit.

### git commit

The second command I ran was git commit -m. -m saves the staged changes as a snapshot in your project’s history. This means your project's version control history has just saved your latest changes in a new version. -m flag lets you leave a message describing what the commit is about, making it easier to review what changed in this version.

### git push

The third command I ran was "git push -u origin master". Using '-u' means you're also setting an 'upstream' for your local branch, which means you're telling Git to remember to push to master by default. 

---

## Authentication

When I commit changes to GitHub, Git asks for my credentials because Git needs to double-check that I have the right to push any changes to the remote origin your local repo is connected with. To do this, Git is now authenticating your identity by asking for your GitHub credentials.

### Local Git identity

It needs a name and email because it uses this information to identify who made each change in a repository. Every time I commit code, Git records my name and email in the commit history. This helps track contributions, especially when working in teams or collaborating through platforms like GitHub. It’s not about authentication it's about attribution. 

When I ran git log, it showed me a detailed history of all the commits made in my local Git repository. Each entry included the commit hash, the author's name and email, the date and time of the commit, and the commit message describing what changes were made. This log helps me track the progress of my project, understand who made which changes, and even revert to previous versions if needed. It's a powerful way to review the development timeline and ensure everything is properly documented.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-github_9a27ee3b)

---

## GitHub tokens

GitHub authentication failed when I entered my password because GitHub phased out password authentication to connect with repositories over HTTPS. There are too many security risks and passwords can get intercepted over the internet, I need to use a personal access token instead, which is a more secure method for logging in and interacting with your repos.

A token in GitHub is a secure, personal access key that I use to authenticate myself when performing Git operations, like pushing or pulling code, from my local machine or remote server. GitHub replaced password-based authentication with tokens to improve security. By using a token, I can safely connect my local Git repository to my GitHub account without exposing my actual password. This is especially useful when working from environments like VSCode or an EC2 instance, where I need to interact with GitHub through the command line or remote tools.

 I followed a few simple steps to securely authenticate Git operations from my local machine or EC2 instance. First, I logged into my GitHub account and navigated to Settings > Developer settings > Personal access tokens. From there, I clicked on "Generate new token", selected the appropriate scopes (like repo for repository access), and set an expiration date. After generating the token, I copied it immediately, since GitHub only shows it once.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-github_fa11169d)

---

## Making changes again

I wanted to see Git working in action, so I updated the index.jsp file. I couldn't see the changes in my GitHub repo initially because I needed to run the command "git push" to send updates to my Git Repo.






To see my changes in my GitHub repository, I had to commit the changes locally using Git and then push them to the remote repository on GitHub. First, I made updates to my web app files. Then, I ran git add . to stage the changes, followed by git commit -m "Descriptive message" to save the changes with a meaningful message. Finally, I used git push origin main (or whatever branch I was working on) to upload the changes to GitHub. Once the push was successful, I could go to my GitHub repo in the browser and see the updated files and commit history.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-github_6becb2bc)

---

## Setting up a READMe file

As a finishing touch to my GitHub repository, I added a README file, which is a text file (usually named README.md) that provides essential information about a project. It’s typically the first thing someone sees when they visit a GitHub repository... I added a README file by  first creating a file named README.md in my project folder. Inside the file, I wrote some basic documentation about my web app, like what it does, how to use it, and any special features I wanted to highlight. Then, I used Git to stage and commit the file with the commands: touch README.md


A README.md file is a special file used to provide information about a project. It’s usually the first thing people see when they visit a GitHub repository. Markdown lets me write formatted documents using plain text. With simple symbols, I can create headings, lists, links, images, code blocks, and more. 

My README file has 6 sections that outline a project focused on deploying a Java-based web application using AWS's CI/CD tools. It begins with an introduction to the project's purpose, automating software release processes through a cloud-based pipeline. The technologies section highlights tools like Amazon EC2 for development, Visual Studio Code as the IDE, and GitHub for version control, with plans to integrate AWS CodeArtifact, CodeBuild, CodeDeploy, and CodePipeline for full CI/CD automation. Setup instructions are provided for cloning the repository and installing dependencies. The README also includes contact information for the project lead, Gabriel Valentine, and concludes with appreciation for NextWork’s guidance, encouraging others to explore the DevOps series through their platform.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-github_c94976902)

---

---
