# Git(Hub) from the ground up

## Git & vesion control introduction

## Git first-time config
At the first time that you will use Git, some configurations need to be done in order to customize your Git enviroment.
### 1. Configure your identity 
First of all, you need to configure your identity, i.e, set your user name and email address. After this step, each commit will have this information, which is important to track who made each commit.
```shell
# config your user name
git config --local user.name "YOUR NAME"
# config your email address
git config --local user.email YOUR_EMAIL
```
### 2. Configure your editor
For doing commits you will need to write a comment (in most cases, a template is mandatory) and for doing that (when you run a _git commit_), Git will open yout system's default editor (notepad, vi, etc). If you want to change the default editor, you can do the following:
```shell
# config your editor
git config --local core.editor "'COMPLETE/PATH/TO/YOUR/EDITOR'"
```
### 3. Configure the commit template
Each commit needs a message and one of the most difficult tasks when working in Git is write good commit messages. A well-crafted git commit message is the best way to communicate **context** about a change to fellow developers (and indeed to their future selves). A diff will tell you **_what_** changed, but only the commit message can properly tell you **_why_**. A good template will make all the things easier.
Look at the repository for hidden files like _.gitcommittemplate_ or _.git_commit_msg_, when you find the correct file, run the following command to configure the template:
```shell
# config your commit template
git config --local commit.template GIT_TEMPLATE_FILENAME
```
### 4. Configure push.default option
From git v1.7.11 release notes: A new mode for push, **simple**, which is a cross between **current** and **upstream**, has been introduced. The command _git push_ without any refspec will push the current branch out to the same name at the remote repository only when it is set to track the branch with the same
name over there. The plan is to make this mode the new default value when **_push.default_** is not configured. So all versions after v1.7.11 will have the option **simple** is the default behavior, but Git will claims about it every time you run a push unless you configure the **simple** option. To do that, do the following:
```shell
# config push default option
git config --local push.default simple
```
If you want to learn more about **_push.default_** option take a look at **_push.default_** section at [git-config](https://git-scm.com/docs/git-config) . 
### 5. Review the configurations
After these 4 steps, you can check your configurations for the local project. Do the following:
```shell
# review configs
git config --local --list 
```
If you want to correct something, just remake one of the previous steps.
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
* http://chris.beams.io/posts/git-commit/ 
