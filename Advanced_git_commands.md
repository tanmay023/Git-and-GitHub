Below is guide to four advanced Git commands:

# git stash
  * Used for temporarily shelve (save) uncommitted changes in your working tree and index so you can sswitch branches or pull without a Work In Progress changes.
  * It saves modified tracked files and (optionally) staged changes and untracked files.
  * Stashes are kept on a stack ( stash@{0} is the newest).
  * `git stash pop` applies the stash and removes it from the stack; `git stash apply` applies but keeps it.

 Common commands and examples:
  * Save tracked changes with a message:
    > `git stash push -m "WIP: experiment on login"`

  * Save including untracked and ignored files:
    > `git stash push -u   # include untracked files` <br>
      `git stash push -a   # include ignored files too...`

  * List stashes:
    > `git stash list`<br>
      ` # putput: stash@{0}: on feature/foo: WIP: experiment on login`

  * Apply the most recent stashes (keep it in stash list):
    > `git stash apply` <br>
      `# or apply a specific stash`<br>
      `git stash apply stash@{1}`

  * Apply and remove from (pop):
    > `git stash pop` <br>
      `# op specific:` <br>
      `git stash pop stash@{1}`

  * Create a branch from a stash (handy when stash contains many changes you want to presserve as a branch):
    > `git stash branch feature/from-stash stash@{0}`<br>
      `# creates and checks out feature/from-stash, applies stash, drop stash on succes`

  * Drop a stash or clear all:
    > `git stash drop stash@{0}`<br>
      `git stash clear`

# Git cherry-pick:
  * Used to apply change introduced by an existing commit (or commits) onto your current branch as a new commit. Use when you want a specific change from another branch without merging the entire branch history.

Common commands and examples:

   * Cherry-pick a single commit:
     > `git checkout main`<br>
       `git cherry-pick abc1234`<br>
       `# creates a new commit on main with the changes from abc1234`

   * Cherry-pick multiple commits (explicit list):
     > `git cherry-pick a1b2c3d e4f5g6h`

   * Cherry-pick a continuous range (commits after A up to and including B):
     > `git Cherry-pick A^..B`<br>
       ` # or simply, list B and earlier commits as needed`

   * Add a referance to original commit (useful fo traceability):
     > `git cherry-pick -x abc1234` <br>
       `# commit message appended with "(cherry picked from commit abc1234)`

   * Do the apply without creating a commit (stage changes only):
     > `git cherry-pick -n abc1234` <br>
       `# then you can edit, stage, and commit manully`

Conflict resolution

 * If the cherry-pick conflicts, Git stops and showa conflicted files
   > `after resolving files:`<br>
     `git add <resolved-files>` <br>
     `git cherry-pick --continue`<br>
     `# or to abort:`<br>
     `git cherry-pick --abort`


# git revert

  * Used to create a new commit that undoes the changes introduced by a specific earlier commit. Safe for undoing public commits because it does not rewrite history, it adds a new commit that reverses the effect.
Common commands and examples:

  * Revert a single commit:
    > `git revert abc1234`<br>
      `# opens editor to edit revert commit message; the new commit undoes abc1234`

  * Revert without opening an editor:
    > `git revert -m  1 abc1234 # -m is used when reverting a merge commit (see below)` <br>
      `git revert --no-edit abc1234`

  * Revert a range of commits (create one revert commit per mommit in the range):
    > `git revert A..B` <br>
      `# note: order matters; this will attempt to revert commits in that set`

  * Revert commits without commiting each each time:
    > `git revert --no-commit A B C` <br>
      `git commit -m "Revert A,B,C"`

 Reverting merge commits
  - Reverting a merge commit requires specify which parent to treat as the mainline ( which parent to keep):
    > `git revert -m 1 <merge-commit-hash>`
  - parent-number 1 means keep the first parent; choose based on how the merge should be inverted.

when to use revert vs reset
 * Use *git revert* on public/sheared branches to undo changes safely.
 * Use *reset* to change local history, not safe once pushed and used by others.
    
