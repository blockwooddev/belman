---
name: git-publishing
description: Commits to github with an branch name and commit message provided by the user as argument. Pushes the commit, grabs the URL to make a Pull Request and provides that back to the user. Use when user requests that changes be committed to a branch in a git repository.
disable-model-invocation: true
---
# Git Publishing Workflow

BRANCH = $0
MSG = $1
1. `git pull origin $BRANCH`
2. `git commit -m "[$BRANCH] $MSG`
3. `git push origin $BRANCH`
4. The response from this command should look like this:
   ```
   Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 12 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 612 bytes | 612.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
remote:
remote: Create a pull request for 'branchname' on GitHub by visiting:
remote:      https://github.com/username/repo/pull/new/branchname
   ```
   Where `https://github.com/username/repo/pull/new/branchname` is the link for a Pull Request. Return this to the user.
5. If the response does not look like the above, prompt the user for input.