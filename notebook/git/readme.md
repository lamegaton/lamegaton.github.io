Create a new repo:  

git init  

Rename local branch:  
https://stackoverflow.com/questions/6591213/how-do-i-rename-a-local-git-branch  

```
git branch -m <oldname> <newname>
```

To check your local branch you can use

```
git branch
```

To check your remote branch

```
git branch -r
```

Rename remote branch:

1. If you invite someone to work with you, they will use

`git clone <https://link_to_your_repo>`

2. They can create a new branch using 

`git branch <lulu>`

3. Then switch to **lulu** using 

`git check out lulu`

4. When **lulu** trying to pull using `git pull`,  she'll have a problem like this 

```
$ git pull
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.
```

So she have to pull from origin

5. Another coworker create a new branch as lala `git branch lala`
6. lala  use `git pull` and have the same error
lala has to use `git branch` and find the 
7. lala has to use `git branch` and find the default
8. Since working, lala has made many contributions, so a manager want to make lala branch as a default branch or master branch
9. Another words, manager want to merge **lala branch** into **master branch**. The manager can archive that by using ``