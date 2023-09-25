---
layout: post
title: "Basic Git commands"
categories: git
author: "Son Pham"
comments: false
meta: how to use git for student or beginner
description: "easy to learn git for beginner and student"
tags: [git]
---

## Creating and Managing Git Repositories

If you're thinking of creating a project for your class, you'll need to create a Git repository. Here are the steps:

1. Create a new repo:
    ```bash
    git init
    ```
    Or in case you are working on a existing repo, you can try
    ```bash
    git clone <repo_location>
    #ex: git clone https://github.com/racket/racket.git
    ```

    To check our remote storage or repo we can try
    ```bash
    git remote -v
    origin  https://github.com/________/________.git (fetch)
    origin  https://github.com/________/________.git (push)
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

5. If you invite someone to work with you on the project, they can clone your repo using:
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

6. When "lulu" tries to pull using "git pull", they may encounter an error message like:
    ```
    There is no tracking information for the current branch.
    Please specify which branch you want to merge with.
    See git-pull(1) for details.
    ```
    In that case, they need to pull from "origin".

    In the same team, another coworker creates a new branch called "lala":
    ```
    git branch lala
    ```

7. When "lala" tries to pull and encounters the same error, they need to use "git branch" to find the default branch.

8. Since working on the project, "lala" has made many contributions, so the manager wants to make the "lala" branch the default or "master" branch. To do this, "lala" needs to add and commit her works:
    ```bash
    git add <lala_works>
    git commit -m "what does lala do"
    ```

9. Then the manager will execute the below commands:
    ```bash
    git checkout master
    git merge lala
    git push origin master
    ```

## Q & A
1. what is the difference between `git pull` and `git fetch`?
    - fetch: get files and store in local branch
    - pull: gets files then merge with current branch. [(ref)](https://stackoverflow.com/questions/292357/what-is-the-difference-between-git-pull-and-git-fetch)

## Tips:

- cherry pick a commit
  - hotfix: something is wrong in our code but other dev found out and push a commit on another branch. So, we are going to cherry pick that commit into our branch.
    ```bash
    git cherry-pick SHA-1
    #ex: git cherry-pick a33e53b322dfba673a0614eca39d39f42c361758
    ```


- If you're tired of typing out commit, add, push separately, you can use a one-liner like this:
  ```bash
  git commit -a -m "commit" && git push
  ```

- What if you has add a new commit and want to revert it?
  ```bash
  #let check the log
  git log
  commit c1797e762814de3863284b5827b92358f26f74c5 (HEAD -> lamegaton)
  Author: Son Pham <testing@gmail.com>
  Date:   Fri May 5 12:43:59 2023 -0400

      change name

  commit 99728dc46e3798cb5a7164697df62fbcdb2dc264 (origin/lamegaton)
  Author: Son Pham <testing@gmail.com>
  Date:   Fri May 5 12:37:02 2023 -0400

      add TOC

  #I want to go back to 
  git revert --no-commit c1797e762814de3863284b5827b92358f26f74c5..HEAD
  git commit

  #or you can try short version
  git log --graph --oneline --decorate
  ```
  [(ref)](https://stackoverflow.com/a/21718540)




