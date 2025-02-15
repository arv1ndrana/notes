# Terms and Definitions
![[git Working dir to Index to HEAD.png]]

| Term                               | Definition                                                |
| ---------------------------------- | --------------------------------------------------------- |
| Repository                         | a functioning place stored as a directory with .git file  |
| Local Repository                   | a folder with .git file in YOUR computer                  |
| Remote Repository                  | an online copy of local repository on server (i.e github) |
| Working Directory                  | holds the actual files                                    |
| [[Index]]                          | acts as a staging area                                    |
| [[How HEAD works in git? \| HEAD]] | points to the last commit made                            |
| Stage                              |                                                           |
| Unstage                            |                                                           |
| Untrack                            |                                                           |
| Staging area                       | preparation                                               |
| [[working tree]]                   |                                                           |
| [[reference]]                      |                                                           |
| [[staged]]                         |                                                           |
| [[upstream]]                       |                                                           |
When using [[git]] to restore file state,
- use `checkout` to restore deleted files.
- use `checkout` to restore file state to desired commit.
- use `reset` to order commits.
- use `revert` to create new commits the same as old commits in servers.

git working mechanism:
- `git init` command adds a `.git` folder in the current folder.
- `git add <file>` or `git add .` command changes the `index` file of the `.git` folder changes
- `git commit -m "<suitable message>"` command stores the `<suitable message>`" in `.git/COMMIT_EDITMSG`
- but, changing `.git/COMMIT_EDITMSG` does NOT change the commit message.

- `HEAD@{1}` means “the previous commit referenced by `HEAD`”, that is, the commit before the merge.

git mantra:
>branch early, and branch often