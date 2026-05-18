- `git branch` can be used to see the branches of git
- `git branch <name>` can be used to create a new branch
- `git switch <branch name>` can be used to switch a branch
- `git rename -m Old_name Newname` can be used to change the name of the branch
- `git branch -d branch_name` can be used to delete the branch

- if the branch is created in local repository we can't commit the branch for that we have to use `git push origin <branch name>`


### Git Merge
- isolating the features into different branches is a crucial practice for any serious developer
- at some point a piece of code will reach a state where we want to integrate it with rest of the project this is where merge comes in
![[Pasted image 20260515172215.png]]

- `git merge <branch name>`
- 


### Revert in Git
- revert is undoing the changes 
- it can be done by RESET or REVERT
- RESET: it is a rollback
- reset points local environment back to a previous commit
![[Pasted image 20260515173042.png]]

- Revert is also rollback but  its approach is different
- revert adds previous commit as a new commit at the end of chain
![[Pasted image 20260515173452.png]]

- `git log --oneline` can be used to list the commit history
- `git reset --soft <commit id>` can be used to roll back to mentioned commit id but it does not delete the changes in the  file only git history is rolled back
- `git reset --hard <commit id>` can be used to roll back the changes too 
- `git revert head` can be used to revert to previous stage


### comparision in git
- `git diff <filename>` can be used to compare the changes in file
- `git diff` shows the differences between staging and working area


