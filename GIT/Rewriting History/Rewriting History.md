## Rewriting History 

**Undoing commits** git reset --soft HEAD^ # Removes the last commit, keeps changed staged git reset --mixed HEAD^ # Unstages the changes as well git reset --hard HEAD^ # Discards local changes 

**Reverting commits** git revert 72856ea # Reverts the given commit git revert HEAD~3.. # Reverts the last three commits git revert --no-commit HEAD~3.. 

**Recovering lost commits** git reflog # Shows the history of HEAD git reflog show bugfix # Shows the history of bugfix pointer 

**Amending the last commit** git commit --amend 

**Interactive rebasing** git rebase -i HEAD~5