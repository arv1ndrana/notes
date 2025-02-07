2025-02-04 01:37

Status: #youth #re-read

Tags: [[git]] [[git theory]] [[cli]]

# How HEAD works in git?
## notes
- *There are 3 types of `HEAD`*
- *`HEAD` can be:*
	- *`.git/HEAD` file*
	- *`HEAD` as in `git show HEAD` (called “revision parameter”)*
	- *`HEAD` in the output of various commands*
- *These are extremely closely related to each other, but not obvious*
- *`.git/HEAD` file contains either:*
	- *name of branch*
	- *commit ID (hash)*
- *`.git/HEAD` file determines the “current branch”* 
- *`.git/HEAD` containing a commit ID instead of a branch is called “detached HEAD state”*
- *`HEAD` in git commands commonly refer to a commit ID*
- *`HEAD`, `HEAD^^^`, `HEAD@{2}` are called “revision parameters”*
- *HEAD in `git show HEAD` [[resolves]] to the current commit you have [[checked out]]!*
- *Git resolves `HEAD` in one of two ways:*
	- *if `.git/HEAD` contains a branch name, it’ll be the latest commit on that branch (for example by reading it from `.git/refs/heads/main`)*
	- *if `.git/HEAD` contains a commit ID, it’ll be that commit ID*
- *The first line of `git status` command's output can look like either:*
	- *`on branch main` means that `.git/HEAD` contains a branch or,*
	- *`HEAD detached at 90c81c72` means that `.git/HEAD` contains a commit ID.*
- *“HEAD is detached” or “detached HEAD state” mean that you have no current branch.*
- *Having no current means new commits will be orphaned!*
- *Orphaned commits are:*
	- *difficult to find (you can’t run `git log somebranch` to find them)*
	- *will eventually be deleted by git’s garbage collection*
- *Getting out of detached HEAD state is easy, you can either:*
	- *Go back to a branch (`git checkout main`)*
	- *Create a new branch at that commit (`git checkout -b newbranch`)*
	- *If you’re in detached HEAD state because you’re in the middle of a rebase, finish or abort the rebase (`git rebase --abort`)*
- *`git log` command's first line of output can be either:*
	- *`commit 96fa6899ea (HEAD -> main)`*
	- *`commit 96fa6899ea (HEAD, main)`*
	- *`commit 96fa6899ea (HEAD)`*
- *inside the `(...)`, git lists every [[reference]] that points at that commit*
- *`HEAD -> main` means that your current branch is `main`*
- *If that line says `HEAD,` instead of `HEAD ->`, it means you’re in detached HEAD state (you have no current branch)*
- *When resolving a merge conflict, a wild `<<<<<<<<<<< HEAD` appears!*
- *When you do a **merge**, `HEAD` in the merge conflict is the same as what `HEAD` was when you ran `git merge`*
- *When you do a **rebase**, `HEAD` in the merge conflict is something totally different: it’s the **other commit** that you’re rebasing on top of. So it’s totally different from what `HEAD` was when you ran `git rebase`*
- *rebase works by first checking out the other commit and then repeatedly cherry-picking commits on top of it*
- ==Similarly, the meaning of “ours” and “theirs” are flipped in a merge and rebase==
- `HEAD` changes depending on whether I’m doing a rebase or merge is confusing so, ignore `HEAD` entirely and use another method
## summary
HEAD can mean 3 different things depending on the context. They all are kind of similar but, are not easily obvious.

The first thing that HEAD can mean is the `.git/HEAD` file.

When reading the `.git/HEAD` file, that is, when using the command `cat .git/HEAD` if the output is a name of a branch then `HEAD` is the current working branch.

But, if the output is a commit ID (hash), you are working in a branch where commits will be orphaned. These types of branch are called "detached HEAD state" or "HEAD is detached".

Orphaned commits are difficult to find and will be automatically deleted by git. So, they can be dangerous if you are not careful.

Handling "detached HEAD state" is easy though. You can just go to a branch using the `git checkout main` command to fix it.

Alternatively, You can create a new branch at that commit using the `git checkout -b <branch>` command where, `<branch>` is the name of the branch.

You can also be in a "detached HEAD state" if you're in the middle of a rebase. This can also be easily fixed by either finishing the rebase or, aborting the rebase using the `git rebase --abort` command.

Secondly, HEAD is commonly referred to commit ID in git commands. The `HEAD`, `HEAD^`, `HEAD~1`, `HEAD@{2}` are called "revision parameters" and are used at the end of commands to specify particular commit.

==The HEAD in `git show HEAD` tries to resolve the merge conflicts by using `git checkout` under the hood to the current commit.== git does so by reading the `.git/HEAD` output and going to that output's printed path of folder if it contains a branch name or, being the commit ID itself when `.git/HEAD` file contains a commit ID.

Lastly, HEAD can mean the output of git commands like `git status` or `git log.

`git status` outputs two types of message.

If `git status` provides the `on branch main` output, it means that `.git/HEAD` contains a branch.

But, if `git status `provides the `HEAD detached at 0as3b23c`, it means that `.git/HEAD` contains a commit ID.

The first line of `git log` can be of three types.

It follows the syntax `commit <hash> (...)`

The `(...)` has every references listed by git that points to a commit of that commit ID (hash).

-`commit 96fa6899ea (HEAD -> main)` means:
- `.git/HEAD` contains `ref: refs/heads/main`
- `.git/refs/heads/main` contains `96fa6899ea`
`commit 96fa6899ea (HEAD, main)` means:
- `.git/HEAD` contains `96fa6899ea` (HEAD is “detached”)
- `.git/refs/heads/main` also contains `96fa6899ea`
`commit 96fa6899ea (HEAD)` means:
- `.git/HEAD` contains `96fa6899ea` (HEAD is “detached”)
- `.git/refs/heads/main` either contains a different commit ID or doesn’t exist

Finally, `HEAD` can appear inside files like `<<<<<<<<<<<<<<<<<<<<<<<< HEAD` when a merge conflict occurs. This `HEAD` is confusing.

==It means when you do a **merge**, `HEAD` in the merge conflict is the same as what `HEAD` was when you ran `git merge`.==

==But, when you do a **rebase**, `HEAD` in the merge conflict is the other commit that you're rebasing on top of, totally different from `HEAD` when you ran `git rebase`==

==`rebase` works by first checking out the other commit and then repeatedly cherry-picking commits on top of it.==
# References
https://jvns.ca/blog/2024/03/08/how-head-works-in-git/