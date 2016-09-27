# Git(Hub) from the ground up

## Git & version control introduction
When working on code for any kind of software project, it is important to track all changes. In fact, keep the records of the work is highly critical and essential when you work at project with multiple developers, all of them will be doing updates at the same code (and sometimes at the same time).

Version Control System (**VCS**) appears as a solution to do this. It consists in a software that helps software developers to work together and maintain a complete and detailed history of their work.  Without this history, it would be almost impossible to work with tens (or even hundreds) of developers on the same project. Additionally, allows the configuration manager to locate bugs and revert the code back to a previous working version.

In general, there are three different models of **VCS** and each one has its particularities.

1. Localized Version Control Systems (**LVCS**)
  * The most common users choice: a single local copy of the project in another directory at the user local machine.
2. Centralized Version Control Systems (**CVCS**)
  * The main concept is that it works in a client and server relationship. The repository is located in one place and provides access to many clients. The most popular tool is **_SVN_**.
3. Distributed/Decentralized Version Control Systems (**DVCS**):
  * Each user has their own copy of the entire repository, not just the files but the history as well. The most popular tools is **_Git_** and **_Mercurial_**.

[Here](http://blogs.atlassian.com/2012/02/version-control-centralized-dvcs/) and [here](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control) you can find more information about each one. This summary will explore a little bit more in **DVCS** (~~because Git uses~~).

**_Git_** uses the third model, **DVCS**. In this model, each developer works directly with their own local repository (i.e, their **fork** of the project) and all changes are shared between repositories as a separate step. Developers can collaborate with different groups of people in different ways simultaneously within the same project. Also, it is important to have in mind that each **fork** of a project consist in a mirror of the main repository, so if the server dies, each developer's repository can be serve as a backup and used to restore the server.

The main benefits of **_Git_** are:
* Powerful and detailed change tracking, which means less conflicts;
* The job can be done offline - except when you are receiving/sending changes to the server;
* Workflow is flexible;
* Data integrity is assured (due to SHA1 trees);
* Branching and merging is more reliable;
* It is very fast.

In other hand, **_Git_** have some drawbacks:
* Steep learning curve;
* Binary files are a big no;
* It is very easy to make mistake until you are familiar with the model and with the workflow.

### Basic concepts
#### Track changes
As presented above, **VCS** is mostly based around one concept: tracking changes that happen within directories or files. Depending on the version control system, this could vary from knowing a file changed to knowing specific characters or bytes in a file have changed.

In **_Git_**, you specify a directory or set of files that should have their changes tracked by version control. This can happen by **checking out** (or **cloning**) a repository from a host, or by telling the software which of your files you wish to have under version control.

The set of files or directories that are under version control are more commonly called a **repository**.

As you make changes, it will track each change behind the scenes. The process will be transparent to you until you are ready to commit those changes.
#### Commiting
As you work with your files that are under version control, each change is tracked automatically. This can include modifying a file, deleting a directory, adding a new file, moving files or just about anything else that might alter the state of the file. Instead of recording each change individually, the version control system will wait for you to submit your changes as a single collection of actions. This collection of actions is known as a **commit**.
#### Revisions and Changesets
When a commit is made, the changes are recorded as a **changeset** and given a unique revision. By knowing the revision of a **changeset** it makes it easy to view or reference it later. A **changeset** will include a reference to the person who made the **commit**, when the change was made, the files or directories affected, a comment and even the changes that happened within the files (lines of code).

When it comes to collaboration, viewing **past revisions** and **changesets** is a valuable tool to see how your project has evolved and for reviewing teammate's code. **_Git_** has a formatted way to view a complete history (**log**) of each revision and **changeset** in the repository.
#### Getting updates
As members of your team **commit** changes, it is important that you have the latest version. Having the latest version reduces the chance of a conflict. Getting the latest changes from a repository is as simple as doing a **pull** from another computer (usually a hosted or centralized server, i.e **GitHub**). When a pull is requested, only the changes since your last request are downloaded.
#### Conflicts
What if the latest update or commit results in a conflict? That is, what if your changes are so similar to the changes that another team member made that **_Git_** can’t determine which is the correct and authoritative change? **_Git_** will provide a way to view the difference between the conflicting versions, allowing you to make a choice. You can either edit the files manually to merge the options, or allow one revision to win over the other. You may want to collaborate with the person who made the other **commit** to make sure you’re not undoing their important work!
#### Diffing
Since each commit is recorded as a change to a file or set of files and directories, it is sometimes useful to view what changed between revisions. By viewing a diff, you can compare two files or even a set of files to see what lines of code changed, when it changed and who changed it. Furthermore, **_Git_** let you compare two sequential revisions, but also two revisions from anywhere in the history.
#### Branching
There are some cases when you want to experiment or **commit** changes to the repository that could break things elsewhere in your code (like working on a new feature). Instead of committing this code directly to the main set of files (usually referred to as **master**), you can create something called a **branch**.
A **branch** allows you to create a copy (or snapshot) of the repository that you can modify in parallel without altering the main set. You can continue to **commit** new changes to the **branch** as you work, while others **commit** to the **master** without the changes affecting each other.
#### Merging
Once you’re comfortable with the experimental code (which means that are no compilation warnings/errors and the changes were tested), you will want to make it part of the **master** again. This is where merging comes in. Since **_Git_** has recorded every change so far, it knows how each file has been altered. By merging the **branch** with the **master** (or even another **branch**), **_Git_** will attempt to seamlessly merge each file and line of code automatically. Once a branch is merged it then updates the **master** with the latest files.

In some cases **_Git_** might not be able to figure out which change to apply between two revisions when doing a merge. If this happens a conflict will arise. A conflict in this scenario is the same as the conflict mentioned above and requires manual intervention to decide which files or lines of code should remain.
#### Pushing
After having gone through all the workflow and your changes are ready to be sent to the repository or to be presented for the configuration manager (in order to review and merge in the server repository), you will perform a **pushing** acting, i.e send the **commits** made on your local branch to a remote repository.

For more information, it is highly recommended to take a time and look at the [tutorials](https://www.atlassian.com/git/tutorials) from [Atlassian](https://www.atlassian.com).

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
