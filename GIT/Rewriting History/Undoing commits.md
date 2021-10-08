### Undoing commits
- ```git reset --soft HEAD^ ```
	-  Removes the last commit, keeps changed staged 
- ``` git reset --mixed HEAD^ ```
	-  Unstages the changes as well 
-  ```git reset --hard HEAD^```
	-  Discards local changes