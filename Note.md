# What is Git?
The world's most popular version control system

Version control is software that tracks and manages changes to files over time.

Version control systems generally allow users to revisit earlier versions of the files, compare 
  changes between versions, undo changes, and a whole lot more.

# Git vs GitHub
## Git
Git is the version control software that runs locally on your machine. You don't need to register for an account.

You don't need the internet to use it. You can use Git without ever touching Github.

## GitHub
Github is a service that hosts Git repositories in the cloud and makes it easier to collaborate with other people.

You do need to sign up for an account to use Github. It's an online place to share work that is done using Git.


# setup
## Name
`git config --global user.name "name"`
## Email
`git config --global user.email "email"`
## Default Editor (VScode)
`git config --global core.editor "code --wait"`

# Terminal Command
## Navigation
`ls`

+ print home directories (shows the files)
start .

+ show folders

`ls folderName/`

+ print folders inside the location

`pwd`

+ print ot your current location

`cd folderName`

+ change location to the folder

`cd ..`

+ take us back one level

`touch fileName`

+ create file

`mkdir`

+ make folder

`rm fileName`

+ remove the file

`rm -rf folderName`

+ remove the folder
+ '-rf' is a version of 'rm' that delete folders

# Repositpry
A Git "Repo" is a workspace which tracks and manages files within a folder.

Anytime we want to use Git with a project, app, etc we need to create a new git repository. 

We can have as many repos on our machine as needed, all with separate histories and contents.

# Git command
## [Official website about command](https://git-scm.com/docs)

## Basics
`git status`

+ gives information on the current status of a git repository and its contents

`git init`

+ Use git init to create a new git repository. 

+ Before we can do anything git-related, wemust initialize a repo first!

## Adding
`git add file1 file2`

+ stage all changes at once

`git add .`

+ this stages all changes at once

## Committing

`git commit -m "Type Messege"`

+ We use the git commit command to actually commit changes from the staging area.

`git commit`

+ go VScode after commit and add comments

`git commit -a -m "message"`

+ this does add and commit at the same time

## Log
`git log`

+ shows the log of commit

`git log --oneline`

+ only shows the first line of comments

# Commit in detail

## Git docs

https://git-scm.com/docs (same as above)

## Atomic Commits

try to keep each commit focused on a single thing.

## writing comment

either past tense or present, be in a pattern

# Amending Commits

`git commit -m "some commit"`

`git add forgotten_file`

`git commit --amend`

+ Suppose you just made a commit and then realized you forgot to include a file! Or, maybe you made a typo in the commit message that you want to correct.

# Ignoring File

`touch .gitignore`

+ Create a file called .gitignore in the root of a repository. Inside the file, we can write patterns to tell Git which files & folders to ignore

# Git Branching 

`git branch`

+ viewing branches

`git branch new-branch-name`

+ Creating branches

+ Use git branch <branch-name> to make a new branch based upon the current HEAD

`git switch branch-name`

+ Switching Branches

`git switch -c new-branch-name`

+ Use git switch with the -c flag to create a new branch AND switch to it all in one go. 

`git checkout branch-name`

+ The checkout command does a million additional things, so the decision was made to add a standalone switch command which is much simpler.

# Deleting & Remaing branches

`git branch -d branch-name`

+ deleting the branch you specify

+ you have to be on the branch somewhere else but not the specigied one

`git branch -m branch-name`

+ rename the branch you specify

+ you have to be on the branch

# Git Merging


We merge branches, not specific commits

We always merge to the current HEAD branch

## Fast Forward merge

`git merge branch-name`
    
1. Switch to or checkout the branch you want to merge the changes into (the receiving branch)
   
2. Use the git merge command to merge changes from a specific branch into the current branch.
  
## Resplving Conflicts
 
1. Open up the file(s) with merge conflicts

2. Edit the file(s) to remove the conflicts. Decide which branch's content you want to keep in each conflict. Or keep the content from both.

3. Remove the conflict "markers" in the document

4. Add your changes and then make a commit!

# Comparing Changes

`git diff`

+ lists all the changes in our working directory that are NOT staged for the next commit.

`git diff HEAD`

+ lists all changes in the working tree since your last commit.

`git diff --staged`

`git diff --cached`

+ list the changes between the staging area and our last commit.

`git diff HEAD file-name`

`git diff --staged file-name`

+ We can view the changes within a specific file by providing git diff with a filename.

`git diff branch1..branch2`

+ list the changes between the tips of branch1 and branch2

`git diff commit1..commit2`

+ To compare two commits, provide git diff with the commit hashes of the commits in question.


# Stashing

`git stash`

+ useful command that helps you save changes that you are not yet ready to commit.

`git stash pop`

+ remove the most recently stashed changes in your stash and re-apply them to your working copy.

`git stash apply`

+ to apply whatever is stashed away, without removing it from the stash. 

+ This can be useful if you want to apply stashed changes to multiple branches

`git stash list`

+ run git stash list to view all stashes

`git stash apply stash@{}`

+ git assumes you want to apply the most recent stash when you run git stash apply, but you can also specify a particular stash like git stash apply stash@{2}

`git stash drop stash@{}`

+ To delete a particular stash, you can use git stash drop <stash-id>

`git stash clear`

+ To clear out all stashes, run git stash clear



# Undoing Changes & Time Traveling

<commit-hash can be replaced by HEAD~# (refers #th commit before)>

`git checkout commit-hash`

You have a couple options:

1. Stay in detached HEAD to examine the contents of the old commit. Poke around, view the files, etc.

2. Leave and go back to wherever you were before - reattach the HEAD

3. Create a new branch and switch to it. You can now make and save changes, since HEAD is no longer detached.

`git checkout HEAD~#`

+ `#` IS NUMBER

+ HEAD~1 refers to the commit before HEAD (parent)

+ HEAD~2 refers to 2 commits before HEAD (grandparent)

+ This is not essential, but I wanted to mention it because it's quite weird looking if you've never seen it.

`git checkout HEAD file-name`

`git checkout -- file-name file-name `

+ to discard any changes in that file, reverting back to the HEAD.

`git restore file-name`

+ To restore the file to the contents in the HEAD (same as "checkout HEAD")

`git restore --source HEAD~# file-name`

+ restore the contents of home.html to its state from the commit prior to HEAD. You can also use a
particular commit hash as the source.

`git restore --staged file-name`

+ If you have accidentally added a file to your staging area with git add and you don't wish to
include it in the next commit, you can use git restore to remove it from staging.

`git reset commit-hash`

+ reset the repo back to a specific commit. The commits are gone. 

+ but changes in files are not gone 

`git reset --hard commit-hash`
  
+ If you want to undo both the commits AND the actual changes in your files, you can use the --hard option.

`git revert commit-hash`

+ git reset actually moves the branch pointer backwards, eliminating commits.



# Cloning

`git clone url`

+ Git will retrieve all the files associated with the repository and will copy them to your local machine.

+ Make sure you are not inside of a repo when you clone!



# Remmote

`git remote -v`

+ To view any existing remotes for you repository

+ This just displays a list of remotes. If you haven't added any remotes yet, you won't see anything!

`git remote add <name> <url>`

+ A remote is really two things: a URL and a label.

+ To add a new remote, we need to provide both to Git.

`git remote rename old-name new-name`

`git remote remove <name>`

+ They are not commonly used, but there are commands to rename and delete remotes if needed.

`git push <remote> <branch>`

+ We need to specify the remote we want to push up to AND the specific local branch we want to
push up to that remote.

`git push <remote> <local-branch>:<remote-branch>`

+ to push our local ranch up to a remote branch of the same name, we dont have to!

`git push -u <remote> <branch>`

+ allwos us to set the upstream of the branch we are pushing. 

+ You can think of this as a link connecting our local branch to a branch on Github.



# Fetching 

`git branch -r `

+ to view the remote branches our local repository knows about.

`git switc <remote-branch>`

+ to create a new local branch from the remote branch of the same name.

`git fetch <remote>`

+ The git fetch <remote> command fetches branches and history from a specific remote repository. 

+ It only updates remote tracking branches. 

`git fetch <remote> <branch>`

+ fetch a specific branch from a remote



# Pulling

git pull = git fitch + git merge

`git pull <remote> <branch> `  

+ To pull, we specify the particular remote and branch we want to pull using git pull <remote> <branch>. 

+ Just like with git merge, it matters WHERE we run this command from.

+ Whatever branch we run it from is where the changes will be merged into.

`git pull`

+ If we run git pull without specifying a particular remote or branch to pull from, git assumes the following:

  -  remote will default to origin

  - branch will default to whatever tracking connection is configured for your current branch.



# ReadMe

[markdown](https://markdown-it.github.io/)



# Rebasing

There are two main ways to use the git rebase command:

- as an alternative to merging

- as a cleanup tool

`git rebase master`

+ Instead of using a merge commit, rebasing rewrites history bby creating new commits for each of the original feature branch commits.

+ Never rebase commits that you have been shared with others If you have alrealdy pushed commmits up to Github... 

+ DO not rebase them unless you are positive o one onn the ream is using those commits

`git rebase -i HEAD~<No.>`

+ runnning git rebase with the -i option will enter the ubnteractive mode, with which allows us to edit commits, add files, drop commits, etc. 

+ Note that we need to specify how far back we want to rewrite commits.

# Tagging

Lightweight tags: They are just a name/lable that points to a particular commit.

Annotated tags: store extra meta data including the another's name and email, the date and a tagging message.

Sementig versioning

<Major>.<Minor>.<Patch>

`git tag`

+ print a list of all the tas in the current repo

`git tag -l "*<filter>*"`

+ print  a list with filter

`git checkout <tag>`

+ detach head at the tag point

`git tag <new tag name>`

+ to create a lighweight tag

+ By default, Git will create the tag referring to the commit that HEAD is referencing.

`git tag -a <new tag name>`

+ to create a new annotated tag. Git will tehn ope your default text editor and prompt you for additional information.

+ Similar to git commit, we can also use the -m option to pass a message directly and forgo the opening of the text editor.

`git show <tag>`

+ to show the annotate of the tag

`git tag <new tag name> <commit hash>`

+ to tag on precious commit

`git tag -f <new tag name>`

+ Git will yell at us if we try to reuse a tag that is already referring to a commit.

+ I fwe use the -f option, we can force our tag through. 

`git tag -d <tag>`

+ to delete a tag

`git push --tags`

+ By default, the git push command does not trasfer tags to remote servers. 

+ If you have a lot  of tags that you want to push up at once, you can yse the --tags option to the git push command.

+ This will transfer all ofyou tags to the remote server that are not already there.

# Reflog 

Git keeps a record of when the tips of branches and other referenes were updated in the repo

<Limitations>
  
Git only keeps reflogs on your local activity. They are not shared with collaborators.

Reflogs are expire. Git cleans out old entries after around 90 days, though this can be configured.

`git reflog show HEAD`

+ The git reflog command accepts subcommands `show`, `expire`, `delete`, and `exists`. Show is the only commonly used variant, and it is the default subcommand.  

+ It will show the log of a specific reference (t defaults to HEAD)

# Aliases
1. Open your terminal application.

2. Type nano ~/.bashrc to open your Bash configuration file in the nano editor.
`alias myalias='mycommand --option'`
  
3. Replace myalias with the name you want to give to your alias, and replace mycommand --option with the command and its options that you want to replace.

4. Save the changes and exit nano by pressing Ctrl+X, then Y, and finally Enter.

5. Reload your Bash configuration by typing source ~/.bashrc in your terminal.

6. Now, whenever you type myalias in your terminal, it will execute the command and options that you assigned to it.
