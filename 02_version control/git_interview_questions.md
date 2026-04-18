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
A commit represents a **snapshot of a project at a specific point in time**. Each commit records the changes made, the author, and a unique identifier. Each commit has a commit message associated with it.

In a typical Git repository, there is a working directory, staging area, and commit history. Each tracks the project's state at various stages.

**Working Directory(aka. untracked )**: Refers to the current, live set of files and directories. This is the version of the project that you actively work on and modify.<br>
**Staging Area (aka. "index" / tracked)**: Serves as a buffer zone. Files in this area are marked for inclusion in the next commit. You control what content moves from the working directory to the staging area.<br>
**Commit History(aka. committed / local repository)** (in the Git directory): Represents the timeline of commits in the form of a versioned archive. It also houses the full content of the project at relevant commit points.<br> 
**Local Repository**: It has the HEAD, which points to your most recent commit.

You can view the commit history using commands such as **```git log```**. This command provides a structured list of commits, detailing the author, commit date, and an associated commit message.
```
# To make a commit with a message
git commit -m "Meaningful Commit"

# To view the commit history
git log
```
## 6. Define branching in Git and its importance.
A **branch** is an independent line of development. It allows you to work on a feature or bug fix, isolate it from the rest of the codebase until it is ready, and then merge it back in

**Main/Master/Trunk/Branch**: The primary branch serving as the project source.

**Feature Branches**: Additional branches dedicated to specific features or tasks, often derived from the Master branch. Each feature branch is an isolated environment for developing a specific feature. This avoids interference with the main codebase.

**Merging**: The process of integrating changes from one branch into another. For instance, integrating finished feature branches into the Master.

**Conflict Resolution**: The act of resolving overlapping changes made to the codebase across different branches.

Importance of branching:
- Collaborative Development: Allows multiple developers to work on the same codebase concurrently, minimizing conflicts.
- Risk Mitigation: Changes are kept separate until they are thoroughly tested. If an experimental feature doesn't work as expected or introduces bugs, it won't affect the more stable Master branch.

## 7. What is a HEAD in Git?
**Local Repository**: It has the **HEAD**, which **points to your most recent commit**. <br>
HEAD identifies the current snapshot/commit in the history tree. Any actions in the working directory or staging area are based on this commit. 

## 8. What does the 'clone' operation in Git do?
- Cloning in Git creates a local copy of the repository, allowing for version control and collaborative work. It establishes a link to a specified remote, permitting fetch and push operations
- The clone command contacts the remote repository, retrieves its history and files, and then saves this snapshot locally
- The clone operation automatically establishes a remote connection, naming it "origin" by default. Should you have multiple remotes or wish to use a different name, configuration adjustments may be required
- After a successful clone, the local repository is configured to interact with a designated remote repository, typically on a centralized server like Github or Bitbucket.
- For GitHub, cloning often uses the HTTPS mode. Upon updates to the remote, the local repository can be synchronized using standard Git commands (e.g., fetch, pull, push).
- Status Verification: Confirming the successful execution of a clone can be done by taking a look at the current remotes via git remote -v, which should display the origin.
```
# initiate the cloning process
git clone <remote-repo-url>

# verify origin setup
git remote -v
```
## 9. How does Git store information?
- The three main components of the Git data structure are the repository, the index/staging area, and the local working copy.

**Git Storage Model**: 
- **Local Working Copy**: Where you directly interact with your files.
- **Staging Area (Index)**: Serves as a sort of "holding area" for changes you want to include in your next commit.
- **Local Repository**: Where Git keeps track of the complete history and stores different versions of your files.

**Repository**: The repository houses the following key components:
- Object Database: Persistently stores snapshots of files and directories as objects, which can be further classified into:
    - Blob objects for individual file contents (SHA-1 hash is based on the file's content)
    - Tree objects that replicate file system hierarchy (SHA-1 hash combines the file and directory contents within—changes in any file or sub-directory would trigger a new hash)
    - Commit objects linked to a specific state in the project's history (SHA-1 hash incorporates the tree representing the project's directory structure, along with parent commit(s), commit message, and author information.)
    - Tag objects marking specific commits, often used for releases.
- Index/Stage: A dynamic workspace that mirrors the next commit's expected state.
- Head Pointer: A reference to the latest commit in your current working branch
- Branches: Human-readable names that reference specific commits, facilitating independent lines of development.

**Git Object Storage**: <br>
Git allows for a 'lazy write' mechanism for objects. This means that an object file is written upon creation and remains unchanged until the content it represents changes. When a change occurs, it gets updated and its SHA-1 is recalculated. <br>
Here's an illustration for better understanding:<br>
Let's assume a file's content changes and you add the updated file to the staging area.
The new version of the file is then stored as a Blob object, and the associated Tree object also gets updated.
During the following commit, a new Commit object is created, which references the updated Tree object.
Simultaneously, the Branch you're working on moves forward to reference this new commit.
This systematic approach assures the integrity of your project's history. Since any alteration in content, directory structure, or commit details will trigger a change in the SHA-1 hash of the related object(s), a change can be immediately recognized.

## 10. How do you initialize a new Git repository?
- Navigate to your project folder using your terminal or command prompt
``` 
git init
```
## 11. Adding Files to the Staging Area
- Use the following command to add files or directories to the staging area:
```
# To add a specific file
git add filename

# To add all files and directories
git add .
```
## 12. Committing Changes
- Once files are in the staging area, use this command to commit these changes:
```
git commit -m "Your commit message goes here"
```
## 13. Associating a Remote Repository
- If you plan to push your local repository to an online service like GitHub, first link your local repository to a remote one:
```
git remote add origin your-remote-repository-url
```
## 14. Pushing to Remote
- Finally, use this command to push your local repository to the remote one:
```
git push -u origin master
```
- After the initial "upstream" link is established, subsequent push commands can be executed with a simple ```git push```

## 15. Handling Sensitive Information
- To ensure that sensitive data, such as API keys or credentials, are not shared, employ the .gitignore file to list files and patterns that should be excluded from version control.
- In particular, avoid using files with such sensitive information before creating a .gitignore.
- Here is the .gitignore file:
```
# Ignored file - example
credentials.txt
```
## 16. Explain the purpose of the ```git status``` command
**git status** is an essential command for tracking changes in a Git repository. It provides important details such as file states, current working branch, tracked and untracked files, and more.

## 17. git reset
- Unstage files that were mistakenly added to the staging area.
```
git reset file1.txt
```
## 18. git checkout
- To remove changes in the working directory, bring them back to the state of the HEAD commit.
```
git checkout file1.txt
```
## 19. Different between ```git push```,  ```git fetch```, ```git pull```
**git push**: (push = “Here’s what I did”)
- Uploads your local commits to a remote repository

**git fetch**:  (fetch = “Let me see what others did”)
- Downloads changes from a remote repository to your local machine
- Does NOT modify your working files

**git pull**: 
- **git pull = git fetch + git merge**
- It fetches changes from the remote and then merges them into the current branch. It can also rebase instead of merge if configured
- Fetches changes from the remote and immediately merges them into your current branch

Best Practice (Mid-Level Thinking): 
- Instead of blindly doing: ```git pull```
- Do this:
    ```
    git fetch
    git log origin/main
    git merge   # or rebase
    ```

**git pull --rebase**: <br>
- **git pull --rebase fetches remote changes and then rebases your local commits on top of them, creating a linear history without merge commits**
- Local main:     **A --- B --- D** (You created commit D)
- origin/main:    **A --- B --- C** (Someone else pushed C) <br>
--> Now your histories have diverged
What Regular ```git pull``` Would Do: 
```
A --- B --- C
       \     \
        D ---- M
```
- You get a merge commit (M)
- History becomes messy

Now: ```git pull --rebase```
- fetch: same as always, git downloads commit C
- rebase begins: It takes commit D off your branch (“Let me temporarily remove your work”)
- it moves your branch to latest remote: Now your branch points to C (A--B--C)
- Git reapplies D on top of C: A --- B --- C --- D'
    - D' = same changes as D, but:
        - new commit hash
        - new position in history
- Final Result: A --- B --- C --- D'   (main)
    - No merge commit
    - Clean, linear history
    - Looks like you worked after C
- If there’s a conflict:
    - Git stops at commit D
    - You fix the conflict
    - Then run: ```git rebase --continue```<br>
    (This can happen per commit, not just once)

## 20. Git branch, git checkout, git merge
- **git branch feature**: 
    - Creates a new branch called feature
    - Points it to your current commit (HEAD)
    - Does NOT switch to it

- **git checkout feature**:
    - Moves HEAD to feature
    - Updates your working directory to match that branch

- **git checkout -b feature**: 
    - Equivalent to: git branch feature + git checkout feature

- **git merge** 
    — combine histories: it takes changes from feature and integrates them into main
    ```
    git checkout main
    git merge feature
    ```

## 21. What is a merge conflict and how to resolve it? 
- A merge conflict occurs when Git cannot automatically reconcile differences between two branches, typically when the same lines in a file are modified. Git marks the conflict in the file, and the developer must manually resolve it before completing the merge or rebase.
- A merge conflict happens when Git can’t automatically decide how to combine changes.
- This usually occurs when:
    - Two branches modify the same line in a file
    - Or one deletes something the other modifies

- How to Resolve a Conflict: 
    - Open the conflicted file
    - Decide the final result: you manually edit it or choose one version, or combine both
    - Remove the markers (No <<<<<<<, =======, >>>>>>> should remain)
    - Stage the resolved file: git add file.txt
    - Complete the merge: git commit (Git often auto-generates the message)

- If conflict happens during rebase:
```git rebase --continue``` instead of ```git commit```

## 22. What is fast-forward merge? 
- A fast-forward merge occurs when the target branch has not diverged, so Git can simply move the branch pointer forward without creating a merge commit.
- It happens when Git can move a branch pointer forward without creating a new commit, there’s nothing to merge—just move the pointer.
- Key insight: 
    - Fast-forward = no new commit, just pointer movement
    - Merge commit = history had to be combined
- Example: 
```
A --- B --- C   (main)
             \
              D --- E   (feature)
```
- feature is ahead of main
- main has no new commits since branching
```
git checkout main
git merge feature
```
```
A --- B --- C --- D --- E   (main, feature)
```

## 23. Explain ```git tag```
- A Git tag is a fixed reference to a specific commit, commonly used to mark release versions. Unlike branches, tags do not move and are used for versioning and release tracking
- A tag is a fixed pointer to a specific commit
```
git tag v1.0
```
- Tags are not pushed automatically, you need to push them:
```
git push origin v1.0 (specific)
git push --tags (all)

git tag (list all tags)
```
- ideal usage for releases or debugging

## 24. How do you revert a commit that has already been pushed to the remote repository?
- For commits that have already been pushed, I use ```git revert```, which creates a new commit that undoes the changes without rewriting history. This is safe for shared repositories.
```
A --- B --- C   (main, pushed)
```
- You want to undo commit C
```
git revert C
```
```
A --- B --- C --- D
                ↑
           revert commit
```
- D cancels out C, but:
    - history stays intact
    - nothing is rewritten
    - safe for teams

- The Dangerous Way: ```git reset + force push```
```
git reset --hard B
git push --force
```
```
Before:
A --- B --- C   (remote)

After:
A --- B         (remote rewritten)
```
- Why This Is Dangerous
    - Rewrites history
    - Teammates may have already pulled C
- Causes:
    - conflicts
    - lost commits
    - confusion

- Special Case: Reverting a Merge Commit: 
```
# You must specify the parent (-m) 
git revert -m 1 <merge_commit_hash>
```

- Real-World Scenario: 
```
# you pushed a bug
git commit -m "broken feature"
git push

# fix it safely:
git revert HEAD
git push
```
- Done. Clean. Professional.

## 25. Explain Gitflow workflow
Gitflow is a branching strategy that uses dedicated branches like main, develop, feature, release, and hotfix to organize development, stabilize releases, and handle production fixes in a structured way.
- Pros:
    - Very structured
    - Clear separation of concerns
    - Good for teams & release cycles
## 26. What is a fork? 
- A fork is a copy of a repository under your own GitHub account
- It lets you experiment or contribute to a project without affecting the original repo
- Key difference:
    - Fork = GitHub-side copy
    - Clone = local copy

- You click: “Fork” button on GitHub
- Now you have: original/repo → your-account/repo (still on GitHub)
- Clone your fork: ```git clone https://github.com/yourname/repo.git```

## 27. What is git stash, how do you view stashed changes? 
- **git stash**: 
    - Git stash temporarily saves uncommitted changes in a stack-like structure, allowing you to switch context without committing. You can later reapply or pop the changes using stash apply or stash pop.
    - is a way to temporarily save your uncommitted changes without making a commit
    - “Put my current messy work aside, let me switch context, I’ll come back later.”
    - Typical situation: You’re working on a feature, and suddenly you need to fix a bug on another branch, but your current work is unfinished. 
    - Instead of committing half-done code: ```git stash```
    - What Actually Happens: 
        - Before: 
            - working directory: modified files
            - staging area: some changes
        - After: 
            - working directory: clean
            - stash: your changes saved internally

- Basic Workflow: 
```
git stash 

# OR more explicitly
git stash push -m "WIP login feature"

# switch branch, fix bug, etc.
git checkout main

# come back and restore
git stash pop
```

- List all stashes: 
```
git stash list
```
- Apply a stash (without removing it): 
```
git stash apply stash@{0}
```
- Apply AND remove: 
```
git stash pop
```
- Delete stash or clear all:
```
git stash drop stash@{0}
git stash clear
```

## 28. How do you view the commit history? 
- you can view commit history using git log, which shows commits in reverse chronological order. Common variants like --oneline and --graph help visualize branches and merges
```
git log
git log --oneline                           (great for quick overview)
git log --oneline --graph --all             (shows branching and merging visually in terminal)
git log -p                                  (shows actual code diff inside each commit)
git log --oneline --graph --decorate --all  (this is what many engineers actually use daily)
```
- Shows full commit history for the current branch.
- Each commit includes: commit hash, author, date, message

## 29. How to find a commit by a specific author in Git? 
```git blame```: 
- Shows which commit last modified each line of a file, useful for identifying who introduced a specific change
- “Who changed this line?”
```
git blame file.txt
```

```git bisect```: 
- Uses binary search through commit history to find the exact commit that introduced a bug by marking commits as good or bad

- Key Insight: 
    - blame → who touched this line
    - bisect → which commit broke everything

## 30. How do you view the changes introduced in a commit?
- To view the changes introduced in a commit, you use ```git show``` or ```git diff``` depending on what exactly you want to inspect 
```
# shows the latest commit (HEAD)
git show

# shows a commit + the exact changes it introduced
git show <commit-hash>

# compare commit vs working directory:
git diff <commit-hash>

# compare last commit vs working tree:
git diff HEAD
```
- Key Insight: 
    - git show → inspect one commit in detail
    - git diff → compare two snapshots

## 31. Can you list the files changed in a specific commit?
```
git show --name-only <commit-hash>
```

## 32. How do you perform a squash commit in Git? 
- Squashing commits means combining multiple commits into a single one, usually using interactive rebase or squash merge, to keep history clean and meaningful.
- **Method 1**: Interactive rebase (most important): 
    ```
    git rebase -i HEAD~3    (Means: “rewrite last 3 commits”)
    ```
    ``` 
    # you will see something like this: 
    pick a1b2c3 first commit
    pick d4e5f6 second commit
    pick g7h8i9 third commit

    # change for this: 
    pick a1b2c3 first commit
    squash d4e5f6 second commit
    squash g7h8i9 third commit
    ```
    - Git combines commits
    - You edit the final commit message
- **Method 2**: Squash during merge
    ```
    git merge --squash feature
    ```
    - this takes all changes from feature
    - applies them as one commit
    - does NOT preserve commit history
- Squashing rewrites history
    - new commit hashes
    - old commits disappear










