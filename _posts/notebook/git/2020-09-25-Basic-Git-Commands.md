---
layout: post
title: "Basic Git commands"
categories: git
author: "Son Pham"
---

#### First, you thinking of create a project for your class so you need to create a repo:  

1.  Create a new repo:  
```git
git init
```

1.  Rename local branch:  
   https://stackoverflow.com/questions/6591213/how-do-i-rename-a-local-git-branch  
```
git branch -m <oldname> <newname>
```
1.  To check your local branch you can use:  
```
git branch
```

1.  To check your remote branch  
```
git branch -r
```

#### The project is expand and you invite someone to work with you  

1.  If you invite someone to work with you, they will use  

`git clone <https://link_to_your_repo>`

2.  They can create a new branch using  

`git branch <lulu>`

3.  Then switch to **lulu** using  

`git check out lulu`

4.  When **lulu** trying to pull using `git pull`,  she'll have a problem like this  

```
$ git pull
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.
```

So she have to pull from origin

5.  Another coworker create a new branch as lala `git branch lala`  
6.  lala  use `git pull` and have the same error, lala has to use `git branch` and find the master branch.  
7.  lala has to use `git branch` and find the default.  
8.  Since working, lala has made many contributions, so a manager want to make lala branch as a default branch or master branch.  
9.  Another words, manager want to merge **lala branch** into **master branch**. To do it lala need to `git add <lala_works>` and `git commit -m "what does lala do"`   
10.  Then manager will `git checkout master` and then `git merge lulu`  

#### Another scenario:  

We assign lala  to work on PHP side only  

#### tips  

If you are tired of commit, add, push, you can try oneliner like this :  
```
git commit -a -m "commit" && git push
```
