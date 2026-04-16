# TOP Interview Questions in Git - with short answers

## 1. What is Git and why is it used?
**Git is a decentralized version control system (DVCS)** that developers primarily use to manage source code across development projects. It ensures better code quality, facilitates teamwork, and provides a robust backup mechanism.

#### Benefits of Using Git: 
- **History and Time Travel**: Git preserves every version of a project, making it possible to roll back changes or inspect code at any point
- **Security and Integrity**: Each file in Git has a unique SHA-1 hash, which means unauthorized changes are easily detected.
- **Collaboration**: Git allows multiple developers to work on a project simultaneously without conflict.
- **Code Reviews**: Git simplifies the process of reviewing code before it's incorporated into the main codebase.

#### Key Concepts: 
- **Commit**: A commit represents a saved state of your project. It is a snapshot of all the files in your project at a given point in time. Each commit has a commit message associated with it.
- **Branch**: A branch is an independent line of development. It allows you to work on a feature or bug fix, isolate it from the rest of the codebase until it is ready, and then merge it back in
- **Master**: is a default branch present in all Git repositories. You can create many other branches.
- **Merge**: Merging in Git means taking the independent developments of two branches and combining them into a single branch. After merging, the two branches from which you were merging are the same as the merged branch.
- **Remote and Origin**: 
    - A remote is a common repository on a server or accessible memory that all team members use to exchange their changes
    - An origin is a source of commit objects (store of all committed versions)

## 2. How does Git differ from other version control systems (VCS)?
- Git offers numerous advantages over traditional Version Control Systems (VCS), providing a **distributed** and efficient version control model.
- Distributed Model: Git decentralized nature empowers every set of files with a complete repository history and enables full-fledged operations without network connectivity. This stands in contrast to centralized systems that require a constant network connection and utilize a single centralized server for all project data.

## 3. What is the difference between Git and GitHub?
**Git** is a version control system for tracking changes of projects, enabling collaboration through different versions, comparing changes, and enabling to revert to previous states. 
- Commit history acts like a detailed logbook, explaining what and why changes were made
- A **git repository** is used to track all changes to files in a specific folder, and keep a history of all changes 
- **Key Features**:
    - Local Management: Developers can work on their repositories without the need for a central server.
    - Speed: Operations such as committing, branching, and merging are rapid, ideal for local development.
    - Staging Area: Changes are first staged before getting committed for better control.
    - Content Tracking: Rather than file-based, Git is content-based, ensuring efficient tracking.

**GitHub** is a cloud-based hosting platform/service that manages git repositories
- **Key Features**: 
    - Remote Repositories: It allows developers to sync their local repositories with remote ones, enabling collaborative work.
    - Code Hosting: Developers can store and manage their code from anywhere, not just their local machines.
    - Collaboration Tools: GitHub provides tools for project management, issue tracking, and team collaboration.
    - Code Review: Multiple users can review and discuss proposed changes before they're merged into the main codebase.
    - Access Control: Different users can have varying levels of access to a repository or organization.

## 4. What is a repository in Git?
- A **git repository** is a location where all the version-controlled files and their history are stored. 
- Every Git repository has two primary parts: the **working tree** and the hidden **.git directory**, where Git keeps all of its metadata for the repository.

## 5. Explain the concept of a commit in Git.







