### Finding a bad commit
- ```git bisect start``` 
- ```git bisect bad```
	- # Marks the current commit as a bad commit 
- ```git bisect good ca49180``` 
	- Marks the given commit as a good commit 
- ```git bisect reset```
	- # Terminates the bisect session