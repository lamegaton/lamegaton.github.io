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
```
git branch -r
```

If you invite someone to work with you on the project, they can clone your repo using:
```
git clone <https://link_to_your_repo>
```

They can create a new branch using:
```
git branch <lulu>
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
- git add <lala_works>
- git commit -m "what does lala do"

Then the manager will:
- git checkout master
- git merge lulu

Another scenario is if we assign "lala" to work on PHP side only.

Tips:
- If you're tired of typing out commit, add, push separately, you can use a one-liner like this:
```
git commit -a -m "commit" && git push
```
