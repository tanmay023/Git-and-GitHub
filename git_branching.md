# Git Branches
* Branch is a movable poilnter to commit. Use to develop features, fix bugs, or try experimentalchanges without affecting mainline history.
* Typical branches are main(or master), develop, feture, bugfix,....

1. git branch --- list, create, delete, rename
   * List local branches:
     > `git branch`

   * List all branches (local +remote):
     > `git branch -a`

   * Create a new branch (does not swith to it):
     > ` git branch feature/login`

   * Create a branch on specific commit or branch:
     > `git branch feature/login origin/main`

   * Delete a local branch:
     >`git branch -d feature/login 		# safe delete (refuse if unmerged)`<br>
	 `git branch -D feature/login 		# force delete`

   * Rename current branch:
     > `git branch -m old-name new-name`

2. git checkout --- switch branches (older command; still ubiquitous)
   * switch to an existing branch:
     > `git checkout main`

   * Create and switch in one step:
     > `git checkout -b feature/login`

   * Restore files from another branch or commit:
     > `git checkout origin/main -- path/to/file`
> Note: `git checkout` does many things (switch, restore). Newer Git seprates behaviors into `git switch` and `git restore` for clear usage.

3. git switch --- modern way to change branches
   * Switch to an existing branch:
     > `git switch main`

   * Create and switch to new branch:
     > `git switch -c frature/login`

   * Switch and setup to track remote branch:
     > `git switch --track origin/feature/login`

4. git merge --- combine another branch into current branch
   * Merge `feature/login` into `main` (first swith to `main`)
     > ` git checkout main`<br>
	 `git merge feature/login`
     - If `main` has no commits since the feature branch diverged, git will fast-forword and move the `main pointer.
     - If both branches have new commits git makes a merge commit by default.

 	* Create an explicit merge commit even if fast-forword is possible:
    	> `git merge --np-ff feature/login`

	* Squash all feature branch commits into single commit on merge (lical history only: this does mot record a branch merge):
     	> ` git merge --squash feature/login` <br>
		`git commir -m "Add login feature (squashed)"`

   Example merge workflow:
  > ` git checkout main` <br>
    `git pull origin main 	# uadate local branch` <br>
     `git merge --no-ff feature/login`<br>
     `git push origin main`

5. git rebase --- reapply on top of another base (rewrite history)
   * Rebase your feature branch onto latest `main`:
     > ` # on feature branch:`<br> `git fetch origin` <br> `git rebase origin/main`
     - This takes commits in `feature` and replys them onto `origin/main`, giving a linear history.

   * Interactive rebase to squash/edit/reword commits:
     > ` git  rebase -i HEAD~4`
     - In the interactive editor you can `pick`, `reward`, `squash`, `fixup`, `drop`, etc.
   * Common rebase workflow before pushing:
     > ` # keep feature up-to-date without merge commits` <br>
	   ` git checkout feature/login` <br>
	   ` git fetch origin` <br>
	   ` git rebase origin/main` <br>
	   ` # fix conflict if any : edit files, then`<br>
	   ` git add <resolved-filed>`<br>
	   ` git rebase --continue` <br>
	   ` # if you want to abort the rebase:` <br>
	   ` git rebase --abort`

   Rebase conflict controls:
   - Continue after resolving conflicts:
     > ` git rebase --continue`

   - Skip current patch:
     > ` git rebase --skip`

   - Abort and return to original branch state:
     > ` git rebase --abort`

  > Important: Do not rebase commit that you've already pushed and that others may have based on (rewriting published history causes problem). For local topic branches or before opening a PR, rebasing is safe and useful.


6. Remote branches --- pushing, setting upstream, deleting

   * Push a new branch and set its upstream ( to future `git push` and `git pull` default to origin/branch):
     > ` git push -u origin feature/login`

   * Push after a rebase (force push required because history changed):
     > `git push --force-with-lease origin feature/login`
     - Prefer `--force-with-lease` over `--force` ---- it's safer for concurrent work.

   * Delete a remote branch:
     > `git push origin --delete feature/login`

7. Viewing branch relationshops and history
   * See a compact graph of history:
     > `git log --online --graph --decorate --all`

   * Check which branch you are on:
     > `git status`

   * See upstream for the current branch:
     > `git rev-parse --abbrev-ref --symbolic-full-name @{u} # show upstream ref (errors if none)` <br>
	   `git branch -vv`
