### Discarding local changes
- ```git restore file.js ```
	- Copies file.js from index to working directory 
- ```git restore file1.js file2.js``` 
	- Restores multiple files in working directory 
- ```git restore.``` 
	- Discards all local changes (except untracked files) 
- ```git clean -fd```
	- Removes all untracked files