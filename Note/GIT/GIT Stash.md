### stashing temporary changes
- git stash temporarily saves changes you've made to your working copy so that you can work on something else and then comeback later and re-apply them
- stashing is handy if you quickly need to quickly switch context and work on something else, but you are midway through a code change and arent quite ready to commit
- `git stash` can be used to create a temporary copy of the current code
- `git stash list` can be used to  see the list of stashed change
- `git stash apply` can be used to resume/ retain the change
- `git stash drop` can be used to drop the stashed file
- `git stash pop` can be used to pop the stashed file from TOS
- `git stash save "message text"` can be used to stash with message
- `git stash show stash@{index}` to find changes done in stash
- `git stash pop stash@{index}` to pop specific file
- 


### Stashing Untracked file
- `git stash -a` can be used to add untracked file to stash too
- 
