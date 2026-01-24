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
    
