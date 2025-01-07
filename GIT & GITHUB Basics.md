## Git & GitHub
Git is a version control system that will help you keep track of the changes and history of your project throughout its lifestyle. I worked through two main components of version control throughout my project:
* Branching - allows you to duplicate the source code for yourself. You will then work on your own branch so your edits do not immediately affect the original source code
* Merging - the process of joining your branch with the original source code after complete testing.

GitHub is the service that will host your Git repositories. Think of GitHub like the cloud server that hosts your source code. The repository for your project consists of all branches, commit, merge history, any licensing or readme files, rake/gem files, etc.
<br/>
The partnership between Git and GitHub grant teams an invaluable asset - any and every modification to code is tracked through the two tools. Therefore, in the case of a mistake the code can efficiently and quickly be rolled back to its previous state prior to the error.
<br/>

### Files Type
* **Untracked Files**: git does not know any about this file. All new files will be considered as a untracked before first time staging (git add).
* **Staged Files**: added to the index and ready to commit or deleted.
* **Modified files**: files which are already tracked and now modified for next commit.
* **Committed files**: files which are inside in Repository.

### Logical Area
* **Working Directory** : All Edited files will be presents working directory.
* **Staging Area** : using a git add command we will move all files to Staging Area.
* **Local Repository** : Current working Repository.

### Repository Type
* **Upstream** : if we fork a copy from any repository, Original source repository will become Upstream
* **Downstream**: our forked copy known as a downstream.

### Definations
* **git revert**: This command creates a new commit that undoes the changes from a previous commit. This command adds new history to the project (it doesn't modify existing history).
* **git checkout:** This command checks-out content from the repository and puts it in your work tree. It can also have other effects, depending on how the command was invoked. For instance, it can also change which branch you are currently working on. This command doesn't make any changes to the history.
* **git reset** This command is a little more complicated. It actually does a couple of different things depending on how it is invoked. It modifies the index (the so-called "staging area"). Or it changes which commit a branch head is currently pointing at. This command may alter existing history (by changing the commit that a branch references).
* **git revert/git reset/git checkout**: If a commit has been made somewhere in the project's history, and you later decide that the commit is wrong and should not have been done, then git revert is the tool for the job. It will undo the changes introduced by the bad commit, recording the "undo" in the history.If you have modified a file in your working tree, but haven't committed the change, then you can use git checkout to checkout a fresh-from-repository copy of the file.If you have made a commit, but haven't shared it with anyone else and you decide you don't want it, then you can use git reset to rewrite the history so that it looks as though you never made that commit.These are just some of the possible usage scenarios. There are other commands that can be useful in some situations, and the above three commands have other uses as well.
* **Branch Name**:branch names can’t contain whitespace: **new-feature** and **new_feature** are valid branch names, but **new feature** is not.
* Git keeps files in Snapshot, it is a incremental backup of files.
* **Resetting vs. reverting** The git revert undoes only one commit while git reset reverts back to the previous project state by deleting succeeding commits.Reverting is considered as safe operation for the commits that have been published to the shared repository. Another advantage of reverting is targeting a specific commit at a random point in the history. Find detailed information about git reset on our next page.

* **Merge/Rebase** **Merge** takes all the changes in one branch and merges them into another branch in one commit.**Rebase** says I want the point at which I branched to move to a new starting point
* **Merge** Let's say you have created a branch for the purpose of developing a single feature. When you want to bring those changes back to master, you probably want merge (you don't care about maintaining all of the interim commits).
* **Rebase** : A second scenario would be if you started doing some development and then another developer made an unrelated change. You probably want to pull and then rebase to base your changes from the current version from the repository.


* **git clean limitations:** By default, the ‘git clean’ command won’t remove.  Another ‘git clean’ command limitation is that developers can’t use it without providing either the –force or –dry-run (-n) switch. If you issue a ‘git clean’ command on its own it will fail and generate an error message similar to “no f’s given
  * historically tracked files;
  * files that are part of an existing commit;
  * files added to the index;
  * new directories; and
  * files listed in  .gitignore
  
* **git log/ git reflog** :  **git log** shows the current HEAD and its ancestry. That is, it prints the commit HEAD points to, then its parent, its parent, and so on. It traverses back through the repo's ancestry, by recursively looking up each commit's parent. **git reflog** doesn't traverse HEAD's ancestry at all. The reflog is an ordered list of the commits that HEAD has pointed to: it's undo history for your repo. The reflog isn't part of the repo itself (it's stored separately to the commits themselves) and isn't included in pushes, fetches or clones; it's purely local.




### git init *directory*
Create empty Git repo in specified directory. Run with no arguments to initialize the current directory as a git repository

  ### git clone _*repo*_
  ```md
  git clone https://github.com/gsmental/demo-repo.git
  ```
The first command you need in order to start using a remote repository is the git clone command. To run the command, after “clone”, put the URL to the server’s .git file. Services like GitHub will give you the repository URL to copy in order to clone a repository.

### git remote add origin *url.. http....git* 
While the clone command is used to get an existing repository from a server, if you want to set up a remote server for a repository you have on your local machine, you will use the remote add command. The first step you need to do is create a repository on a server. On GitHub, do this going to your Repositories tab in your profile, and click the “New” button.On your local machine, if you don’t have a repository setup, you can initialized a new repository with the following commands in Git Bash.
 ```git
echo "# demo-repo" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/gsmental/demo-repo.git
git push -u origin main
  
 ```
Now, in the repository, you can run the “git remote add *name* *url*”. The name is the name reference for the server, which is typically “origin”. The URL value can be grabbed off the GitHub page where you set up the empty repository. After you add the remote server, you can move you local repository to the server. When you push, you will be asked to authenticate, and after that, you will see a message like the one below.
 

### git push / git push origin *branch*
 ```git
 git push -u origin master or git push --set-upstream origin master
 ```
It will push all your changed and set Default origin for next time. then there is no need to type origin again and again. In the example above, the “-u” flag was used. That flag is actually short hand for “--setup-upstream”.

### git fetch
The fetch command is used to update any references to remote branches or tags. This means the you will bring those changes down from the remote server, and the local repository will be aware of the changes that have occurred, but the changes will not be made to the local repository branches.
Let’s say you are working on a project and you are on branch “foo-bar”, which is on you local machine. You have also pushed this branch to the remote, and a friend/co-worker is also working on the branch. The other person working on the branch commits some changes and pushes them to the remote. He then tells you about the changes, and you run the command, “git fetch”. The changes will come down, and you will get a message similar to the following;
```git
 Your branch is behind 'origin/foo-bar' by 1 commit, and can be fast-forwarded. 
```
You may have some commits in your local repository on the same branch that you have not yet pushed to the remote repository. In that case, you’d see a message similar to the following.
 ```git
 Your branch and 'origin/foo-bar' have diverged, and have 3 and 1 different commits each, respectively. 
 ```
The main take away for the “fetch” command is to remember that you have the references of the changes from the remote branch, “origin/foo-bar” in the example, but they are not in your local repository yet. The next command will be used to get those changes into your local repository. 
 
### git pull
The pull command is used to take any changes that have occurred on the remote repository, and move them into you local repository. When you run “git fetch”, the reference of the changes on the remote come down to you local repository. When you run “git pull”, you actually put the changes into your repository.
It is usually a good practice to follow to run “fetch” before you run “pull”, so you can see what is actually coming into your branch — you can check the remote repositories logs if you want to, but usually seeing if there are any commits should be enough to know what you are putting in your local repository.
As mentioned above, there can be a point when you fetch the latest code for a branch on the remote, and you discover that you local branch the the remote have diverged. In cases like this, you can pull the changes from the remote into you local branch, but in order to do so, you need to create a merge commit. If there are merge conflicts, you will need to resolve them before you are able to pull — merge conflicts happen when the same file has changes on the same line and git doesn’t know what changes should be used.

### Pull Requests
A pull request is a feature of GitHub and other source code management tools that allow a repository’s collaborators to review and give feedback on proposed code changes before they are accepted and merged to another branch, usually the main branch. Each pull request creates a discussion forum that can be used by reviewers and authors alike to highlight or add comments to a single line of code or chunk of code, add videos or images, etc.<br/>Going through the pull request process can increase group knowledge, improve product quality, and develop professional skills through group critique  
  
### GIT BASICS
| Command|Description |
| --- | --- |
|git status|This command will show the status of the current repository including staged, unstaged, and untracked files.|
|git archive master --format=zip --output=file.zip|ZIP Archive of Master branch. There are two format as  zip, tar| 
|git add *filename/directory*| Stage all changes in particular directory/file for the next commit|
|git add .|Stage all changes in directory/files for the next commit|
|git branch -d *branchName*|Checks merge status before deleting and gives warning|
|git branch -D *branchName*|Does the force deletion of a local branch.|
|git branch *newBranchName*|It will create new branch of sourced repository. It will copy all commits of sourced branch into new branch.|
|git branch|List of all branches in your local repository|
|git branch -d **branchName**|It will delete branch permanently from local repository and before deletion you have to checkout any other branch like master.|
|git branch -m currentBranchName newname<br/>git push origin branch3|Rename/move of particular branch in local repository then we can push this new branch to remote, but old branch (branch2) will be unaffected in remote.|
|git branch -m branch2 branch3 <br/>git push origin :branch2 branch3|we rename  branch2 with branch3, we will also push in this style so that remote branch will be also renamed with new name and all commits will be merged with new  branch.| 
|git commit -m "Title" -m "Description"|Commit the staged snapshot and it save this commit on local machine. this is ready to push to online repository.|
|git commit -a -m| "commit message"	Combines the -a and -m options for creating a commit for all the staged changes and taking an inline commit message.|
|git commit –amend|*git commit –amend* flag allows you to update a commit. To avoid creating a new one, you could create your changes, stage them with git add and then type the command git commit --amend to update your previous commit.The terminal editor will ask you to update your commit message.</br>
*git config --global alias.glop "log --pretty=format:"%h %s" --graph"*</br>*git glop*|*Git aliases*:If you have a set of commands that you use regularly and want to save some time from typing them, you can easily set up an alias for each command using Git config.|
|git config user.name "Mona Lisa"|Set a Git username|
|git config user.name|Get username|
|git config --global user.email "email@example.com"|Setting your email address for every repository on your computer|
|git config --global core.editor Vim|Set the default editor|
|git config --global alias.co checkout|Set up an alias for each command|
|git config --global alias.br branch|Set up an alias for each command|
|git config --global alias.ci commit|Set up an alias for each command|
|git config --global alias.st status|Set up an alias for each command|
|git clean|only removes untracked files. By default, ‘git clean’ won’t touch directories or files listed in the .gitignore file.|
|git clean -n|	The -n option performs a try out of git clean. It shows the files that are going to be removed, but doesn’t remove them. Git wants you to first run the command with the -n option to force a dry run.| 
|git clean -f|	The --force option is required unless the clean.requireForce configuration option is set to false. It deletes untracked files from the current directory, except the untracked folders or files specified with .gitignore.|
|git clean -d| 	-d switch will cause directories to be deleted|
|git clean -f -d|	to remove untracked directories;|
|git clean -f -x|	-d switch will cause directories to be deleted, and the -x switch will force the deletion of ignored files:|
|git clean -i|	switch to do an interactive|
|git checkout *newBranchName*|It will leave existing branch and switched to new branch|
|git checkout -b *BranchNew*|Checkout and switch to new branch. New Branch will be created from  HEAD|
|git checkout -b *BranchNew* *CommitId*|Create new branch from COMMITHASH|
|git checkout -b *BranchNew* *HEAD~4*|Create new branch from 4 commits prior to head|
|git checkout HEAD scene-5.txt<br/>git diff|*Rolling Back to Last Commit*:  In Git, the *git checkout HEAD filename* command rolls back all changes that have been made to *filename* since the last commit. In other words, this command will change your working directory to look exactly as it did when you last made a commit.<br/>You can use the *git diff* command to see if the rollback was successful. If git diff doesn’t output anything, this means your working directory matches your last commit.|
|git diff **filename**|It will compare difference with staged and local modified file. It will show what is changed and from which it changed in same file.|
|git diff **filename1** **filename2**|It will compare local repository difference between two files|
|git diff --cached **filename**|It will compare difference with remote and local modified file. It will show what is changed and from which it changed in same file.|
|git diff CommitId1 CommitId2|It will compare two different Commits in local repository|
|git diff CommitId fileName|It will compare file with commit in repository|
|git ls-files|List of tracked files in repository|
|git log|List of all committed |
|git log –oneline|oneline flag condenses each commit to a single line. By default, it displays only the commit ID and the first line of the commit message.|
|git log --oneline master|Logs from specific branch|
|git log -3|only the 3 most recent commits.|
|git log --after="2014-7-1"||	
|git log --after="yesterday"||
|git log --after="2014-7-1" --before="2014-7-4"||	
|git log --author="John"||	
|git log --grep="JRA-224:"|To filter commits by their commit message, use the --grep flag. This works just like the --author flag discussed above, but it matches against the commit message instead of the author|
|git status|Also show current branch in which you are working now|
|git merge *FromBranchName*|It will merge all changes from Branch to my current working branch.|
|git rebase *sourcebranch*|If source branch has update with any new changes, it will update my current branch from source(parent) branch. Only new comments will be merged with current branch.|
|git rm --cached *File*|To unstage file from staging area and file will be move to untracked.| 
|git remote origin|To see all available commands|
|git remote remove origin|All remote tracking/branches/configuration will  be removed with remote server. Like we use *git remote remove origin <url>* to connect a repository. <br/>Then **remote -v** If you see no fetch/push response that mean repository is removed from remote.|
|git push origin --delete **branchName**|It will delete particular branch from  remote permanently. No code/commit will be available.|
|git push -f origin **branch**|It is used to push forcefully changes to remote. **This should be avoided it might be override other’s commits.**|
|git fetch<br/>git diff master origin/master|It will compare branch with remote branch|
|git pull origin main|Lets you copy all the files to Local Repository from  Remote Main Branch.|
*git merge origin/branch-name*|In Git, the git merge origin/branch-name command will merge fetched changes, stored in origin/branch-name to the current branch-name branch|
|git restore --staged *fileName*|It will unstage files which are already marked as a staged with *git add .*|
|git reset <br/> git reset --mixed|	All staged files will be become unstaged. *--mixed and reset* alone are same command.|
|git reset --hard|	It will revert all changes which happen from previous commit. New files will be deleted and modified files will be revert back to previous commit.|
|git reset *commit_SHA*|In Git, the *git reset commit_SHA* command can be used to set HEAD to the commit_SHA commit. The commit_SHA argument is the first seven digits of a previous commit’s SHA. In this example, the HEAD was reset to the commit made on   specific Day. You can use *git log* to see a record of previous commits and their SHA values.|
git add filename_1 filename_2|*Staging Multiple Files*: In Git, the *git add filename_1 filename_2* command is used to add multiple files to the staging area at once. You can use *git status* to check if you properly added your files to the staging area.|
|git reset HEAD *filename*|*Remove File from Staging*: In Git, the *git reset HEAD filename* command will remove filename from the staging area. Note that this command does not discard file changes from the working directory. You might use this command if you’ve added a file to the staging area, but the file includes incorrect edits.<br/>You can use the git status command to make sure your file was properly removed from the staging area.|
|git remote -v|By using this, we can see remote server repository with configuration|
|git show|Will show previous commit|
|git show *first 5 digit of CommitId*|git show will show all detail about commit and what is changed from previous commit|
|git show HEAD|The output of the git show HEAD command will display everything the git log command displays for the HEAD commit, plus all the file changes that were committed.|
|git stash<br/> git stash pop|*git stash*: allows you to get back to a clean commit point with a synchronized working tree, and avoid losing your local changes in the process of switching branches or tasks.<br/>You’re “stashing” your local work temporarily in order to update a previous commit and later on retrieve your work.You can use *git stash pop* to retrieve from your stash.|
 
 
 ### GIT Error with Solutions
| Error|Solution |
| --- | --- |
|! [rejected]        main -> main (non-fast-forward)</br>error: failed to push some refs to 'url'| git reset --mixed origin/main</br> add ./...commit/push|
