2025-02-08 19:38

Status: #todo 

Tags: 

# What does dirty and clean working directory mean?
![[clean working tree showcase with git status command.png]]
## notes
- Clean working directory means there are no **tracked and modified** files in the local git repository.
- When you make changes to a file that git is tracking, git sees that there is a difference between the current state of the file and the last committed state of that file. Until this file is committed, `git status` will show this file as modified and your working directory will be dirty.
- Tracked files are files that git knows about. That is, files that you have previously made a snapshot of by using `git add <file_name>` and `git commit`.
- 


## summary



# References
https://stackoverflow.com/questions/34571498/what-does-dirty-clean-working-directory-mean
https://stackoverflow.com/questions/39128500/working-tree-vs-working-directory