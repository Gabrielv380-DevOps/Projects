<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Secure Packages with CodeArtifact

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-codeartifact-updated)

**Author:** Kenmore Valentine Sandoval  
**Email:** gabrielv380@gmail.com

---

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-codeartifact-updated_1d79e699)

---

## Introducing Today's Project!

Today, I'm here to walk through a full-stack cloud development workflow using AWS. I started by launching an EC2 instance and setting up my Java web app directly on it. Then, I connected my app’s code to a GitHub repository to enable version control and collaboration. Now, I’m setting up AWS CodeArtifact to manage and store my app’s packages. This includes creating a CodeArtifact repository, configuring my EC2 instance with the right permissions to access it, and verifying that the repository is storing my packages correctly. Each step brings me closer to building a fully automated and scalable CI/CD pipeline in the cloud.

### Key tools and concepts

In this project, I learned how to work with several key AWS services and package management concepts. First, I got hands-on experience with AWS CodeArtifact, which allowed me to securely publish, store, and manage custom packages. I also used AWS CloudShell, a browser-based command-line interface, to run commands for packaging, hashing, uploading, and downloading my project assets. Through this, I learned how to generate a SHA-256 hash to validate the integrity of my package and how to inspect its contents after downloading.

On the Maven side, I learned how to configure the pom.xml file for deployment, set up authentication with CodeArtifact, and manage dependencies effectively. I also gained a deeper understanding of the package lifecycle, from creation and publishing to consumption and validation. Overall, this project helped me build confidence in using cloud-based tools for secure and efficient package management.

### Project reflection

This project took me approximately 2 hours. The most challenging part of this project was learning how to properly configure and interact with AWS CodeArtifact using the command line in CloudShell. Understanding the flow of authentication, package publishing, and repository setup took some trial and error, especially when dealing with Maven settings and ensuring everything was correctly aligned. It was also a bit tricky to validate the package and confirm that it had been published and downloaded successfully.

However, it was most rewarding to see my custom package go through the full lifecycle, from creation and publishing to downloading and validation. Being able to inspect the package contents and confirm its integrity using SHA-256 hashing gave me a real sense of control and confidence in the process. It felt great to apply cloud-based tools in a hands-on way and see everything come together smoothly.

This project is part three of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tomorrow.

---

## CodeArtifact Repository

CodeArtifact is a secure, central place to store all your software packages. When you're building an application, you typically use dozens of external packages or libraries - things other developers have created that you don't want to build from scratch. Engineering teams use artifact repositories because it  gives you a consistent, reliable place to store and retrieve these components. 

Creating and configuring a new CodeArtifact repository today is an important step in organizing and managing the packages and dependencies for my Java web application. By setting up a domain in CodeArtifact, I can group multiple repositories under one umbrella, which makes it easier to share packages across different projects and control access more efficiently. This setup also simplifies how my EC2 instance and other AWS services interact with the repositories, since they can use a single domain endpoint. Overall, using a domain helps me scale my package management strategy and keep everything organized as my application grows.

A CodeArtifact repository can have an upstream repository, which means When your application looks for a package that isn't in your CodeArtifact repository, CodeArtifact will check its upstream repositories (like Maven Central in our case) to find it.  

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-codeartifact-updated_n4o5p6q7)

---

## CodeArtifact Security

### Issue

We need an authorization token to access AWS CodeArtifact because it ensures secure and controlled access to the repository. When I connect tools like Maven to CodeArtifact, the token acts as a temporary credential that verifies my identity and permissions. This helps prevent unauthorized access and protects the integrity of the packages stored in the repository. AWS generates these tokens through its authentication system, and they typically expire after a set period, which adds an extra layer of security. Without the token, my EC2 instance or build tools wouldn’t be able to retrieve or publish packages to CodeArtifact.

### Resolution

I resolved the permissions error by creating a custom IAM policy that granted my EC2 instance access to AWS CodeArtifact. Then, I made a new IAM role and attached that policy to it. After assigning the role to my EC2 instance, I re-ran the export token command, and this time, it worked successfully. The error occurred because my instance lacked the necessary permissions to authenticate with CodeArtifact, and setting up the IAM role with the correct policy resolved that issue.

Using IAM roles is considered a security best practice because it allows me to grant temporary, scoped permissions to AWS resources without embedding long-term credentials in my code or configuration files. When I attach an IAM role to my EC2 instance, AWS automatically provides secure access to services like CodeArtifact through short-lived credentials. This reduces the risk of credential leaks and simplifies access management. It also makes it easier to rotate permissions and audit access, helping me maintain a secure and compliant cloud environment.

---

## The JSON policy attached to my role

The IAM policy I created grants my EC2 instance the necessary permissions to access AWS CodeArtifact. Specifically, it allows actions like retrieving an authorization token, reading from the repository, and downloading packages. These permissions are essential because without them, my EC2 instance wouldn’t be able to authenticate with CodeArtifact or use tools like Maven to pull dependencies. By setting up this policy, I’m ensuring secure and seamless communication between my instance and the repository, which is a critical part of automating my build and deployment process.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-codeartifact-updated_23rp7q8r9)

---

## Maven and CodeArtifact

### To test the connection between Maven and CodeArtifact, I compiled my web app using settings.xml

The settings.xml file enables Maven to work with AWS CodeArtifact by storing the configuration details Maven needs to authenticate and connect to the repository. In my case, it includes the authorization token, repository URL, and profile settings that tell Maven where to fetch dependencies from and how to securely access them. Without this file, Maven wouldn’t know how to communicate with CodeArtifact, especially since it requires temporary credentials and specific endpoints. By setting up settings.xml correctly, I ensure that my build process runs smoothly and that all dependencies are pulled directly from my CodeArtifact repository.

When I run mvn -s settings.xml compile, Maven first checks the dependencies listed in my project's pom.xml file. Instead of pulling them directly from public repositories, it looks in my CodeArtifact repository. If a dependency isn’t already there, Maven fetches it from the upstream repository—Maven Central in my case—caches it in CodeArtifact, and then delivers it to my project. This happens for each required dependency, making my build process more secure, controlled, and faster for future builds since the dependencies are already cached.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-codeartifact-updated_c17eace8)

---

## Verify Connection

After compiling my web app using Maven with CodeArtifact configured as the repository, I checked the CodeArtifact repository to see what had been cached. I found that all the dependencies listed in my pom.xml file had either been retrieved from CodeArtifact directly or, if they weren’t already present, fetched from Maven Central and then stored in CodeArtifact. The repository displayed a Maven-style structure, organizing dependencies by group ID, artifact ID, and version. Each cached dependency included metadata such as the source, version, and timestamp. This setup not only ensured that my build process was secure and controlled, but also made future builds faster since the dependencies were already available in CodeArtifact and didn’t need to be downloaded again.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-codeartifact-updated_1d79e699)

---

## Uploading My Own Packages

In this mission, I’ll be creating my own custom Java package from scratch, defining its structure and functionality to suit a specific purpose. Once the package is ready, I’ll publish it directly to my AWS CodeArtifact repository, making it available for use across other projects. This involves configuring Maven to deploy the package securely and efficiently. After publishing, I’ll complete the full package lifecycle by downloading my own package into a separate project, verifying that it integrates correctly and functions as expected. Throughout the process, I’ll document each step to showcase advanced package management skills, including repository setup, dependency handling, and lifecycle management, demonstrating a strong grasp of modern development workflows.

To generate my own package, I used the AWS CloudShell in the AWS Console. I started by creating a .tar.gz archive of my custom project—this included all the source files and metadata I wanted to package. Then, I ran a command. This command calculated the SHA-256 hash of my archive and stored it in an environment variable called ASSET_SHA256. This hash acts as a unique fingerprint for the package, which is useful for verifying its integrity and ensuring that the contents haven’t been altered. After generating the hash, I used it as part of the process to publish the package to my CodeArtifact repository, completing the first phase of the package lifecycle.

When I visited the package details page in CodeArtifact, I saw several key pieces of metadata about the package I had just published. First, it showed the exact time the package was published, which confirmed that the deployment had just occurred. It also displayed the version information I had defined in my pom.xml, helping me track and manage different releases. Since this was an original package that I created and published directly, the origin was listed as the current repository, there were no upstream sources involved. Additionally, when I clicked into the version number and scrolled down to the Assets section, I found the security hashes that were automatically calculated for the package. These hashes, including the SHA-256 I had generated earlier, help verify the integrity of the package and ensure it hasn’t been tampered with.

To validate my package, I went back into AWS CloudShell and ran the command to download the package I had previously published to CodeArtifact. Once the package was downloaded, I used another command to inspect its contents and confirm that everything was included as expected. This allowed me to verify the structure of the package, ensure the files were intact, and confirm that the metadata matched what I had originally defined. By checking the contents directly, I was able to validate that the package was correctly built, securely stored, and ready for use in other projects.

![Image](http://learn.nextwork.org/compassionate_maroon_festive_yak/uploads/aws-devops-codeartifact-updated_sm12-upload)

---

---
