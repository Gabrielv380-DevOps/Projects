<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up a Web App in the Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-vscode)

**Author:** Kenmore Valentine Sandoval  
**Email:** gabrielv380@gmail.com

---

## Set Up a Web App Using AWS and VS Code

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-vscode_7a1de541)

---

## Introducing Today's Project!

I'm doing this project to learn about how CI/CD works 

### Key tools and concepts

Services I used were VS Code and Amazon EC2. Key Concepts i learnt include SSH connctions using an IDE, launching an instance, editing an index.jsp file and using key pairs.

### Project reflection

One thing I didn't expect in this project was the secret mission where I also used the local terminal to try and edit a file after using an IDE. It was fun to compare the difference in experience and also still see the changes made over the terminal.

This project took me approximately 2.5 hours. The most challenging part was when my SSH connection wasn't working with my key pair, so I had to start all over from scratch. It was most rewarding when the SSH connection was successful.

This project is part one of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tomorrow!

---

## Launching an EC2 instance

I started this project by launching an EC2 instance because EC2 instances are like computers that live in the cloud. I want my web app to live entirely in the cloud, so I am launching an EC2 instance to even develop my Web app's code.

### I also enabled SSH

SSH is the protocol that authorizes users like myself to access remote servers like EC2 Instances its also the type of traffic that allows me to transfer data back and forth to the EC2 instance. I enabled SSH so that I can securely connect to my EC2

### Key pairs

A key pair is a mechanism for me to connect toget acess  to EC2 instances we launch in AWS I've created a Key Pair for the EC2 instance that I am launching key pair works by having two halves, a private key and a public key

Once I set up my key pair, AWS automatically downloaded the private key file called nextwork-keypair.pem. ive moved that file into a folder called DevOps on my desktop

---

## Set up VS Code

VS Code is one of the most popular IDE in the world as an IDE Engineers use it to manage their coding projects

I installed VS Code to write and edit our web app's code.  it also have handy extension that let me directly connect to my EC2 instance so i can write an edit code that will live inside the instance.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-vscode_53d05e68)

---

## My first terminal commands

A terminal is A terminal is where you send instructions to your computer using text instead of clicks. The first command I ran for this project is cd C:\Users\KenmoreSandoval\Desktop\DevOps


I also updated my private key's permissions by running the command icacls "nextwork-keypair.pem" /reset
icacls "nextwork-keypair.pem" /grant:r "KenmoreSandoval:R"
icacls "nextwork-keypair.pem" /inheritance:r
this command gives us access to connect 

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-vscode_9328ada1)

---

## SSH connection to EC2 instance

To connect to my EC2 instance, I ran the command ssh -i ( path to private key) ec2 user @ ipv4 address of EC2 instance. this command sets up an SSH connection directly between my local computer and the instance

### This command required an IPv4 address

A server's IPV4 DNS is the public address for your EC2 server that the internet uses to find and connect to it.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-vscode_e3069dca)

---

## Maven & Java

Apache Maven is a tool that helps developers build and organize Java software projects. It's also a package manager, which means it automatically downloads any external pieces of code your project depends on to work.

Maven is required in this project because it will help us set up all the necessary web files to create a web app structure, allowing us to jump straight into the fun part of developing the web app sooner.

Java is a popular programming language used to build various types of applications, ranging from mobile apps to large enterprise systems.

Java is required in this project because if we don't install Java, we won't be able to use Maven to generate/build our web app today.

Amazon Corretto 8 is a version of Java that we're using for this project. It's free and reliable.

---

## Create the Application

I generated a Java web app using the command mvn archetype:generate \ . This command tells Maven to generate a web app using an existing template that it has. it also tells Maven to call the generated web app project " nextwork-webapp-project"

I installed Remote - SSH, which is an extension via VS Code. This extension lets me connect VS Code directly to a remote server like an EC2instance.

Configuration details required to set up a remote connection include the host name (i.e, the EC2 instance's address) the identity file (i.e the location of our private key) and the user (i.e the user that we're logging into for our instance

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-vscode_2939cf01)

---

## Create the Application

Using VS Code's file explorer, I could see a bunch of folders and subfolders that define my web app.  folders can be expanded by clicking on all of the angled brackets >

Two of the project folders created by Maven are src and webapp, which the src (source) folder holds all the source code files that define how your web app looks and works.src is further divided into webapp, which are the web app's files, e.g., HTML

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-vscode_45f91fd7)

---

## Using Remote - SSH

index.jsp is a file used in Java web apps. It's similar to an HTML file because it contains markup to display web pages. However, index.jsp can also include Java code, which lets it generate dynamic content that's always changing.

I edited index.jsp by updating the HTML code to say        " Hello Gabriel". I also added a paragraph (i.e, some text that says  "This is my NextWork web application working!"

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-vscode_7a1de541)

---

## Using nano

---

---
