---
name: git-publish
description: Commits to github with an branch name and commit message provided by the user as argument. Pushes the commit, grabs the URL to make a Pull Request and provides that back to the user. Use when user requests that changes be committed to a branch in a git repository.
disable-model-invocation: true
---
# Git Publishing Workflow

BRANCH = $0
MSG = $1
1. `git pull origin $BRANCH`
2. `git commit -m "[$BRANCH] $MSG`
3. `git push origin $BRANCH`
4. Return the pr_url from this to the caller: 
```shell
  github_url=`git remote get-url origin`
  branch_name=`git symbolic-ref HEAD | cut -d"/" -f 3,4`;
  pr_url=$github_url"/compare/main..."$branch_name?expand=1
  echo pr_url
```
