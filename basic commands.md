# Basic Git Commands
1. `git init`
   * It create a new local Git repository in the current directory. It creates `.git` folder that stores repo metadata.
   * Used to track an existing project locally.
   * Example:
   		> `cd my-projectd` <br>
  		> `git init` <br>
   		> `git add . `<br>
   		> `git commit -m "Initial commit" `

2. `git clone`
   * This command is used to copy remote repository to your local machine( creates local repo ans sets `origin` remote)
   * Used to get a local copy of a remote repo.
   * Example:
   		> `git clone https://github.com/owner/repo.git`<br>  
   		> `git clone https://github.com/oowner/repo.git my-local-folder` `# clone into specific directory`

3. `git status`
   * This command shows the state of your working directory and staging area(which files are staged, modified, untracked,etc)
   * Used to check what changed before adding or commiting.
   * Example :
     	> `git satus`<br>
      > ` git status -s` `# short format`

4. `git add`
   * This command stage changes (new files, modification, deletions) so they will be included in next commmit.
   * Use after editing file, before `git commit`.
   * Example :
     	> `# stage a single file`<br>
       `git add REDEME.md`<br>
       ` # stage all changed files (tracked and new)`<br>
       `git add .`<br>
			 `# stage a folder`<br>
       `git add src/`<br>
			 `# stage parts of file interactively`<br>
			 `git add -p file.txt`

5. `git commit`
   * This command record a snapshot of the staged changes to the repo history(local only).
   *  Use after staging what ypu want to save.
   *  Example :
     	> `# create a commit with a message`<br>
       `git commit -m "Add User login features"`<br>
       `# if you forget to stage changes, you can commit all tracked changes directly:`<br>
      `git commit -a -m "update config"`<br>
			`# amend the last commit (useful to changes message or add missed files)`<br>
			`git commit --amend -m "Corrected commit message"`

6. `git push`
   * This command upload your local commits to a remote repository(pushes branch refs).
   * Use share your commits with others / upload to origin.
   * Example :
     	>`# push the current branch to origin(default branch name e.g., main)`<br>
			`git push origin main`<br>
			`# push and set upstream (first push of a new branch)`<br>
			`git push -u origin feature/new-ui`<br>
			`# push all branches:`<br>
			` git push --qll origin`

7. `git pull`
   * This command changes from a remote and merge them into the current branch(short for git fetch + git fetch).
   * Use to upsate local branch with remote changes before you start working or before pushing.
   * Example :
     	> `# pull the current branch from origin and merge`<br>
			`git pull origin main`<br>
			`# pull and rebase (keeps a linear history)`<br>
			`git pull --rebase origin main`<br>
			`# simply fetch without merging`<br>
			`git fetch origin`<br>
			`# then inspect or merge manually`<br>
			`git merge origin/main`
	
