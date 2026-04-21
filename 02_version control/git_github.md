# Version Control - Git and GitHub

### Version Control (source control, revision control): 
- **primary goal is to keep track of changes**
- is a system for tracking and managing changes to files over time, commonly used in software development to record every modification of source code 
- it allows teams to collaborate efficiently, revert to previous versions if errors occur, and compare changes, ensuring code integrity and project history is maintained
- VCS allows developers access to the entire change history with the ability to revert or roll back to a previous state
- is safety net to protect the source code from irreparable harm, giving the development team the freedom to experiment without fear of causing damage or creating code conflicts

#### Benefits of using VC: 
- **revision history**: it provides a record of all changes in a project, it has the ability to revert to a stable point in time in case of issues or bugs, so the team can work faster and deliver code with more confident
- **identity**: all changes were made with the identity of the user
- **collaboration**: a developer works with many people on the same project, everyone can submit their own code and review other's code (peer review) to provide feedback
- **automation**
- **efficiency**

### Types of Version Control Systems:
- **Centralized VCSs (CVCS):**  
    - Contains a central server where the complete project history is stored and clients are users
    - Developers must connect to this server to access and update the code
    - Pros: 
        - easier to learn
        - give more access control to user
    - Cons:
        - slower (needs to estabilish a connection to the server to perform any actions)

- **Distributed Version Control System (DVCS)**: 
    - Similar to CVCS, you still need to pull code down from the server to view the latest changes
    - The key difference is that every user is essentially a server and not a client. This means that every time you pull down code from the distributed model, you have the entire history of changes on your local system
    - **Each developer has a full copy of the project history on their local machine, enabling offline work and faster operations**.
    - Pros:
        - it allows users to work in an offline state (you don't need to be connected to the server to add your changes or view a file's history, users can work in an offline state, you only have to connect to server when you pull down or push back the changes)
        - speed and performance is better 
        - better software developement life cycle

- **Version Control Systems examples:**
    - Distributed: Git, Mercurial 
    - Centralized: Subversion, Perforce
    - AWS Code Commit (distributed VCS that acts as a centralized managed repository)

### Git
- is a version control system for tracking changes of projects, enabling collaboration through different versions, comparing changes, and enabling to revert to previous states. 
- Commit history acts like a detailed logbook, explaining what and why changes were made
- A **git repository** is used to track all changes to files in a specific folder, and keep a history of all changes 

### GitHub
- is a cloud-based hosting platform/service that manages git repositories

## Version control in professional software development 
- Version Control plays a crucial part in software development
- Developers work together to deliver software to customers
- VC must be completed by other tools and procedures to ensure quality and efficiency throughout the process

### Common tools and startegies to complete VC:
- **Workflow**:     
    - a good workflow is a must, to **avoid/resolve merge conflicts** (when developers work on the same files)
- **Peer reviews** - another developer review the code before it is merged

- **Continuos Integration (CI)**: 
    - is used to automate the integration of code changes from multiple developers into a single main stream. 
    - Small changes are merged frequently will reduce the number of merge conflicts
    - This process is widespread in test-driven software development strategies
    - CI is used to automatically compile the project and run tests on every code change to ensure that the build remain stable

- **Continous Delivery (CD)**: 
    - is built on top of CI
    - When changes are merged into the main codebase, a Continous Delivery pipeline automates the process of preparing the application for deployment
    - This process includes tasks like building the aplication, running tests, preparing it for deployment to production-like environment
    - The main goal of Continuous Delivery is to ensure that the application is always in a deployable state
    - Continuous Delivery requires manual approval to release the application to the production environment. Although this gives teams greater control over when and how changes are deployed to live systems, Continuous Delivery is slower than Continuous Deployment because of this manual step

- **Continuos Deployment**: 
    - it takes Continuous Delivery a step further by automating the actual deployment of the application to production
    - With this practice, every change that passes through automated tests and validations in the pipeline is automatically deployed to production without the need for manual intervention. 
    - Unlike Continuous Delivery, Continuous Deployment eliminates the manual approval step, making it faster and more efficient. 
    - This approach ensures that updates, features, and fixes are delivered to customers as soon as they are ready, fostering rapid and iterative delivery 

The **Continuous Delivery** steps ensure the code is production-ready after passing all tests and reviews. 
The **Continuous Deployment** then automates the final step of deploying production-ready code without manual intervention. Using them together in a production environment provides an additional safety layer but also increases the time required.

#### Short: 
- **Continuous Integration** is used to automatically integrate code changes
- **Continuous Delivery** automatically packages the application and prepares it for deployment
- **Continuous Deployment** helps to deploy the application to customers frequently

### Staging vs. Production
**Deployment environments**:<br>
before a team release their new feature or changes, they need to verify that the code is not going to cause any issues or bugs. So they set up multiple environments for testing and verifying. (UAT, QA and staging environments). The more ways to test the changes the less likely bugs will be introduced.<br><br>
**Staging:** 
- this should mimic the production environment
- This allows teams to find any potential issues prior going production
- **Areas that benefit from staging environments**:
    - **New features**: developers submitting **new features with feature flags** for turning them on and off in staging environment. The team can verify that the feature works as expected and does not break other functionalities. 
    - **Testing**: staging mimics the production, so testing is a must at this point. QA teams will apply Unit testing, Integration tests and Performance test. 
    - **Migrations**: Snapshots can be taken from production and used to test your migration scripts to confirm your changes will not break anything.
    - **Configuration changes**<br><br>

**Production**: 
- Production is live. It's out there for people to see. Any issues or problems should have been caught and fixed in the staging environments. 
- Downtime: if users can not access your website or app to its full capabilities, it will most likely have a cost involved
- Vulnerabilities: Cyber-security should also play a big role in what gets released in production. Any updates to software such as patching or moving to the latest version should be checked and verified. This is also the same rule for not upgrading software when critical updates are released.
- Reputation: Downtime or issues in production is damaging for a company as it does not instill confidence in end users. If something is down or broken it can cause the company to lose potential customers

## Git / GitHub Questions

### Connecting to GitHub via HTTPS
When you connect to a repository via HTTPS, its required to authenticate using a **Personal Access Token**. 
A Personal Access Token is a special password that you use instead of your actual account password. When you're finished using the token, you can revoke it so that it can no longer be used. It is also possible to set an expiry time for the token. This helps to keep your account secure.
- **Generate a Personal Access Token:** 
    - Profile --> Settings --> Developer Settings
    - Personal access tokens --> Tokens (classic) --> Generate new token (classic)
    - Set the Name and Expirations date 
    - Select scope: click 'repo' 
    - Generate token 
    - Make sure to copy and keep note of the token, as it will be hidden when you leave the page
    - This token now can be used when connectiong to repository over HTTPS

### Connecting to GitHub via SSH: 
If you plan to use Github from your local device, the recommended way to authenticate is using Secure Shell, or SSH for short. This requires the creation of keys: a public and a private key. The advantage of using SSH is that you don't need to enter in your credentials when interacting with the remote repository. The keys are generated and stored on your local machine and then the public key is copied to the Github server. After you finish setting up, every operation will be authenticated using the keys.
- **Generate SSH keys**:
    - open Terminal, and type: ```ssh-keygen -t ed25519 -C "your@email.com"```
    - it will prompt to enter a password. Hit enter to skip setting a password and do the same for entering the same passphrase again.
    - the keys have been created and stored in the .ssh folder
    - In order to add our key to Github, we need to get a copy of the public key which is always identified as .pub in your local directory
    - then use the below command to copy the file, replacing the <YOUR KEY> with the name of the key file on your device.
    ```
    ls ~/.ssh/
    pbcopy < ~/.ssh/<YOUR KEY>.pub
    ```
- **Adding your keys to GitHub**: <br>
    We now need to add our public key to Github to grant access to the repositories we create:
    - Profile --> Settings --> SSH and GPG keys
    - Click on 'New SSH keys', add title and copy the key
    - You are now ready to access Github via SSH.

### Git workflow:
(When I clone the repository, and check the content of it, there is a '.git' folder. It is a hidden folder (ls -la) and used to track all of the changes. This folder is automatically created when you create a repository. It is initialized by running the '**git init**' command. As the repository was created on GitHub, it is not required to run the 'git init'. GitHub handled all of this as part of its 'create new repo' flow.)

- **Working directory / Modified**: adding, removing or updating files. Git knows the file has changed, but does not track it. 

- **Staging area / Staged:** in order for Git to track a file, it needs to be put in the staged area (use **git add** to add files from untracked to tracked state)

- **Committed**: committing a file in Git is a save point in many ways. Git will save the file, and have a snapshot of the current changes. (**git commit -m "commit message"**)

- **Remote repository**: we push our commits into the remote repository (on GitHub) (**git push**)

![alt text](/02_version%20control/screenshots/git_local_remote.png)
![alt text](/02_version%20control/screenshots/cheatsheet.png)


### Branches:
- Before creating a new branch, make sure that your branch is up to date with the 'origen/main', and nothing to commit, working tree clean 
```
git branch feature/lesson               - it will create the new branch 
git checkout -b feature/lesson          - it will create and checkout to this new branch
git branch                              - it shows all of my branches, and my current stay
```
- Use git push to push your changes from the local repository to the remote repo
```
git push -u origin feature/lesson
```
### Pull Request 
- Once you are ready with your feature branch, changes need to be merged back to the main branch. --> You create a PR
- When you create a **pull request** you are asking the other developers to review (**peer review**) your work and approve it to be merged to the repository
- Once PR is approved, you can merge the changes into main branch
- Having independent branches makes the project easier to manage
- This is cleaner than everyone working on the main branch, which could likely cause a lot of isses / merge conflicts.
- Also there is no limit how many branches you can have
- Once you pushed your changes from feature into main on GitHub UI, go back to your Terminal
```
git status                          - you are still on feature, chackout to main
git checkout main
git pull (git fetch + git merge)    - you will recieve the latest changes from your main remote repository 
```

### Remote vs. Local
- **Remote repository** where any developer can push their changes(GitHub). 
The remote code is accessed through a URI which is unique and only accessible to those who have permission.
- **Local repository** refers to your machine which can be a laptop, desktop or mobile device, and it is only accessible to you.
- One advantage is using git that you can work offline and commit your changes when you are ready. 
You need internet connection to push or pull the changes between local and remote. 
- **Let's create a new local repository with git init**:
```
mkdir my-first-repo
cd my-first-repo
git init                    - an empty git repository has been initialized
git remote                  - it comes back as blank 
```
- 'git remote' comes back blank, the reason for that is that I've only initialized a local repository which has no connection to a central repository yet. Right now it's only available locally on my machine. 

### Cloning repository through GitHub CLI
- in Terminal navigate to the folder where you want to clone your repo, than:
```
gh auth login
> GitHub.com
> SSH
> Yes
> How would you like to authenticate GitHub CLI? Login with a web browser

First copy your one-time code: 8963-6140
Press Enter to open github.com in your browser... 
```
- type the one time password, and authenticate yourself through Authentication App




