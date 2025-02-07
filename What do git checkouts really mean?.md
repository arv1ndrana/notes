2025-02-04 03:09

Status: #todo #technical

Tags:

# What do git checkouts really mean?
## notes
- `checkout` to a particular branch means `HEAD` points to that branch
- `HEAD` is a label noting where you are in the commit tree
- `HEAD` moves with you when you move from one commit to another
- `git checkout <commit>` is the basic mechanism for moving around in the commit tree, moving your focus (`HEAD`) to the specified commit
- The commit can be specified by any of a number of ways, commit hash, branch name, tag name, the relative syntax (`HEAD^`, `HEAD~1`, etc.) and so on.
- ==It is often useful to consider a checkout to be changing branches, and there are some options that work from that perspective, but they all [[reference]] commits.==
- To checkout a commit has some side effects other than moving `HEAD` around.
	- The working directory is updated to the state of the checked out commit.
	- if a branch name is specified, checkout makes that branch active. The active branch will move along with any new commits that are added.
	    - with the `-b` option a new branch will be created based on the current commit and then made active.
	    - with the `--track` option the checked out branch can be made aware of a remote branch
	    - with the `--orphan` option a new branch is created (like with `-b`) but will not be based on any existing commit.
- If you're on a branch, the branch name is the latest commit for that branch -- if you're not on a branch, you are on the latest commit.
- ==please note that `git checkout <commit> <path>` does not switch branches.==
- Let say we have folder named `dev` and `index.html` also Everything is tracked and working directory is clean.
- If I accidentally change file name `index.html` and I want to undo that i will simply use `git checkout index.html` it will recover that file state from repository currently selected branch.
- Now if I made some change in `dev` folder and want to recover that. I can use `git checkout dev` but what if there is already branch named `dev` instead of checking out that folder it will pull down that branch. To avoid that I would rather do `git checkout -- dev`.
- Now here bare double dash stands for current branch and asking git for folder `dev` from currently selected branch.
- Similarly If I do `git checkout alpha dev` it will pull down dev folder from alpha branch.
- "To check out" means that you take any given commit from the repository and re-create the state of the associated file and directory tree in the working directory.
- When you check out a commit that is _not_ a branch head (e.g. `git checkout HEAD~2`), you are on a so-called _detached_ head. You can create commits here, but once you switch to a different branch, those commits will not be recoverable by a branch name and might even get removed by the garbage collector after some time.

## summary
The `checkout` command points the `HEAD` to a particular branch. [[How HEAD works in git?|HEAD]] is a label noting where you are in the commit tree. `HEAD` moves with you when you move from one commit to another.

`git checkout <commit>` is how you move around in your [[commit tree]]. Moving your1 focus that is the `HEAD` to a specified commit.

Here, the `<commit>` can be:
- commit hash
- branch name
- tag name
- relative syntax (e.g `HEAD^`, `HEAD~1`) a.k.a revision parameter
- and so on

==The `checkout` command also updates the state of the checked out commit in the working directory.==

The `git checkout <branch>` command makes the newly checked out branch, active. ==The active branch will move along with any new commits that are added.==

The `git checkout -b <branch>` command makes a new branch based on the current commit and then made active.

==The `git checkout --track <branch>` command makes the checkout out branch aware of a remote branch.==

According to the commit tree,
If you are on a branch, the branch name is the latest commit for that branch.

==But, if you are not on a branch, you are on the latest commit.==

**NOTE**: `git checkout <commit> <path>` does not switch branches.

Example Use Case
We have folder named `dev` and a file named `index.html`.
Everything is tracked and [[working directory is clean]].

The file `index.html` is renamed or deleted.
You can undo it by using `git checkout index.html` command to ==repository's currently selected branch file state.==

Similarly, The contents of the folder `dev` is changed.
You can undo it by using `git checkout dev` command to repository's currently selected branch folder state.

But, what if you have a branch named `dev`
The git command prioritizes branches above folders.

So, doing `git checkout dev` in the case of having both `dev` folder and `dev` branch will switch your branch to `dev` instead of undoing your changes.

To avoid this, do `git checkout -- dev` to undo your changes in the `dev` folder instead of switching your branch to `dev`.

Here, the `--` mean the current branch.

Similarly, doing `git checkout dev index.html` will changes the file `index.html` in the current branch to the state of the file `index.html` from the branch `dev`.


# References
https://stackoverflow.com/questions/15296473/what-do-git-checkouts-really-mean