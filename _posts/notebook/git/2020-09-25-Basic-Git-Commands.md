---
layout: post
title: "Basic Git commands"
categories: git
author: "Son Pham"
---

## Creating and Managing Git Repositories

If you're thinking of creating a project for your class, you'll need to create a Git repository. Here are the steps:

1. Create a new repo:
```bash
git init
```

2. Rename local branch:
```
git branch -m <oldname> <newname>
```

3. To check your local branch, you can use:
```
git branch
```

4. To check your remote branch, use:
```bash
git branch -r
```

To check all branches you can use
```bash
git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/frjaraur
  remotes/origin/master
```

If you invite someone to work with you on the project, they can clone your repo using:
```
git clone <https://link_to_your_repo>
```

They can create a new branch using:
```
git branch lulu
```

Then switch to the new branch using:
```
git checkout lulu
```

When "lulu" tries to pull using "git pull", they may encounter an error message like:
```
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.
```
In that case, they need to pull from "origin".

Another coworker creates a new branch called "lala":
```
git branch lala
```

When "lala" tries to pull and encounters the same error, they need to use "git branch" to find the default branch.

Since working on the project, "lala" has made many contributions, so the manager wants to make the "lala" branch the default or "master" branch. To do this, "lala" needs to:
```bash
git add <lala_works>
git commit -m "what does lala do"
```

Then the manager will:
```bash
git checkout master
git merge lulu
```
Another scenario is if we assign "lala" to work on PHP side only.

## Tips:
- If you're tired of typing out commit, add, push separately, you can use a one-liner like this:
```
git commit -a -m "commit" && git push
```

- What if you has add a new commit and want to revert it?


```bash
#let check the log
git log
commit c1797e762814de3863284b5827b92358f26f74c5 (HEAD -> lamegaton)
Author: Son Pham <sonpham995@gmail.com>
Date:   Fri May 5 12:43:59 2023 -0400

    change name

commit 99728dc46e3798cb5a7164697df62fbcdb2dc264 (origin/lamegaton)
Author: Son Pham <sonpham995@gmail.com>
Date:   Fri May 5 12:37:02 2023 -0400

    add TOC

#I want to go back to 
git revert --no-commit c1797e762814de3863284b5827b92358f26f74c5..HEAD
git commit

#or you can try short version
git log --graph --oneline --decorate
```
https://stackoverflow.com/a/21718540




