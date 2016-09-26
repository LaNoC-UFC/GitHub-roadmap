# Git(Hub) from the ground up

## Git & vesion control introduction

## Git first-time config

## GitHub contribution workflow
GitHub supports the *Fork & Pull request workflow* that allows you to propose patches to a repository which you don't have write access. The general procedure is very simple:

1. You fork the repository to your account (using the Fork button on github.com);
2. You clone the repository from your account to your machine (using git bash);
3. You checkout to a new branch to make the mods (using git bash);
4. You make the changes, add and commit them (using git bash);
5. You push the new branch to your github account (using git bash); and
6. You make a *pull request* of that new branch (on github.com).

Bellow each step is explained more deeply.
### 1. Fork the upstream repo
As you don't have write access to the upstream repository you have to fork it to your account (for which you'll have write rights). You do it using the **Fork** button on the upstream repository at github.com. Now if you go to your github homepage you'll see the upstream fork there.
### 2. Clone your fork
As you'll probably make the changes on you computer you have to clone your fork to it. You can do it either using ssh or https.
```shell
# using https
git clone https://github.com/YOUR-USER/YOUR-FORK.git
```
You'll want to keep your local main branch (normally 'master' or 'develop') up to date with the upstream main branch. To do so add a remote pointing to upstream repository.
```shell
# Add 'upstream' repo to list of remotes
git remote add upstream https://github.com/UPSTREAM-USER/ORIGINAL-PROJECT.git
```
To syncronize it do a fetch then rebase:
```shell
# on MAIN-BRANCH-NAME
git fetch upstream
git rebase upstream/MAIN-BRANCH-NAME
```
You'll want to do it before creating a new branch.
### 3. Checkout to a new local branch
Don't make changes on your local main branch. Instead create a new branch to implement your mods.
```shell
git checkout -b NEW-BRANCH-WITH-MEANINGFUL-NAME MAIN-BRANCH-NAME
```
### 4. Implement the changes
ToDo
### 5. Push your branch to your github account
Once you have finished your mods and made commits, you can rebase them on top of upstream main branch.
```shell
# on NEW-BRANCH-WITH-MEANINGFUL-NAME
git fetch upstream
git rebase upstream/MAIN-BRANCH-NAME
```
And finally, you can send it to your github account.
```shell
# on NEW-BRANCH-WITH-MEANINGFUL-NAME
git push origin NEW-BRANCH-WITH-MEANINGFUL-NAME
```
### 6. Make a pull request
On your github account page go to your fork and click on 'branches'. You'll see a **New pull request** button on the right side of NEW-BRANCH-WITH-MEANINGFUL-NAME. Click on it and write a good explanation of your patch purpose.

## Good Practices & Tips

## References & Resources
* https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup
* https://gist.github.com/Chaser324/ce0505fbed06b947d962/
* http://blog.adamspiers.org/2015/03/24/why-and-how-to-correctly-amend-github-pull-requests
