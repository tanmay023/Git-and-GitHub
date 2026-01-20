# Git-and-GitHub

## Git Introduction

Git is a distributed version control system (VCS):- 
which track the changes in source code during development. 
It helps developers to collaborate, manage different versions of code and roll back changes as required.
### Properties of Git
- *Open source and free.*
- *Public and private repository hosting*
- *Allow to work a standalone program, a client, or a sever*
- *Distributed Architecture*
- *Fast and efficient*
- *No dependancy on central sever*
- *Allows collaboration, history tracking, branching & merging, distributed development, incremental changes*

### Core Concepts of Git
1. **Repositories** <br>
   We can also call it repo. It is a storage, where your project files and their history stored.
   There are two types of repositories in Git:
   - Local Repository: It is copy of project on our local machine.
   - Remote Repository: version of project on a server, also platforms like Github, Gitlab, or Bitbucket.

2. **Commits** <br>
It is version of project at specific point in time. Each commit has a unique identifier (hash) and include message describing cahnges.  Commit allow to review and track history of project.

3. **Branches** <br>
It allows developers to work on sepreate tasks, without affecting main codebase. <br>
Common branch's:
- ***Main (or Master) Branch***: Stable version of project, usualy production-ready.
- ***Feature Branch***: Used for developing new features or bug fixes.

4. **Merging** <br>
It is process of integrating from one branch into another branch. Allows us to combine the work done in different branches and resolve any conflicts that arise.

5. **Cloning** <br>
Cloning a repository means creating local copy of remote repository. It includes all files, branches, and commit history.

6. **Pull and Push** <br>
- ***Pull***: Feches updates from remote repository and integrates them into our local repository.
- ***Push***: Sends our local changes to remote repository, and makes them available to others.

## The Three States in Git (the stagine area concept)

Git manages your work through three local areas: <br>
> > Working Directory  →  Staging Area  →  Repository (.git)
     (edit)              (select)          (save permanently)

1. **Working Directory**<br>
This is actual folder on our computer, where we edit files, write code, deletes files, modify content.<br> Changes here are not yet recorded by Git, it only notices something is changed, does not save automatically. [ Changes not staged ]

2. **Staging Area**<br>
It is temporary holding area, here we decide exactly which changes should go into the next commit.<br> This gives us fine control over our commits, we can commit only part of our work and can group releated changes logically.

3. **Repository (.git directory)** <br>
This is like database where Git permanently store commits, this is hidden .git folder. After commiting  all changes are stored safely in Git history.



