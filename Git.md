- To ensure consistency, clone an continue with the .git folder
- `git status --ignored`
- `git status -u` for untracked files
- `git add .`  to add all files not on .gitignore
- `git remove rm -r --cached` to remove recursively all files on .gitignore from repository while keeping local copies
- Check line 
- `touch [filename]`
- `rm [filename]` removes listed files and deletes local copies
- `git log [branchname]` shows history
- `git remote -v` View existing remotes
- `git remote set-url origin https://github.com/user/repo2.git` Set remote
- `git mv` to rename file.
- `git reset HEAD <file>` Unstage a staged file
- `git fetch <repo>`
- `pb git://github.com/paulboone/ticgit.git` You can now use the string pd in lieu of the URL
- `git remote show [remote-name]` Inspect remote
- `git remote rename` rename remote
- `git tag` List tags
- `git tag -l 'v1.4.2.*'` Search tags (Supports regex)
- `git tag -a v1.4 -m 'my version 1.4'` Annotated tag
-  `git config --global alias.unstage 'reset HEAD --'` You can use aliases to make commands clearer.
- `git checkout -b [branch-name]` Switch to a new branch name. This is a shorthand for `git branch [branch-name]` followed by `git checkout  [branch-name]` 
- 


# PAD & Git

- `mkdir -p /mnt/dq/Obsidian` 
- `mount -t ios null /mnt/dq/Obsidian`
- `cd /mnt/dq/Obsidian/`
- 