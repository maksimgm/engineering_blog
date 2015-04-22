# Gitting Work Some Done

This piece examines some essential git commands. Some basic terminology will be provided for those who are not familiar with git syntax. Below every definition, is the git command used to complete the task.
=======
# Gitting Some Work Done

In this piece I will discuss two basic, but essential, commands in Git: `git push` and `git pull`. Additionally, some basic terminology will be provided for readers who are not very familiar with Git syntax. Below every definition is a Git command which must be entered in order to complete the given task.


## git push

This command pushes files from your local Git repository to GitHub. Bear in mind that, this command will only push files that are already in your git repository, not upload files from your staging index, or working directory E.g.

	$ git push origin master

## git pull

This command pulls the latest changes from the remote repository on Github to your local repository (i.e. on your local machine). E.g.

	$ git pull origin master
        
Note: Files should never be edited directly on Github. They should always be edited locally on your machine, then added, committed and pushed to your remote repository where they can be collaborated on.

## git add

This command adds files from your **Working Directory** to your **Staging Index**. Once files are added to your Staging Index, Git begins tracking them. In contrast, files in the working directory are untracked. E.g.

add all files: 

	$ git add .
	
add specific files: 

	$ git add ‘file.txt’


## git commit

If you are satisfied with your changes in the **Staging Index**, commit your changes to the Git repo by using this command. The commit message should contain information about the changes made to the file. i.e. If I edit an HTML file by adding a new head, E.g.
        
	$ git commit -m ‘add head to HTML’

An ideal commit message should be clear and brief; do not write anything unnecessary . E.g.

	$ git commit -m ‘initial commit'
=======
If you are satisfied with your changes in the Staging Index,
commit your changes to the Git repo by using this command. The 
commit message should contain information about the changes made to the file. i.e. If I edit an HTML file by adding a new head, E.g.
        
	$ git commit -m ‘add head to HTML’

An ideal commit message should be clear and brief; do not say write anything you don’t have to. E.g.

	$ git commit -m ‘type commit message’ // This is bad


## git log

This commands gives the user in-depth information about a commit. The list of commit messages are displayed starting with the most recent commit on the top. Inside the commit, you will find info about: the author, date, commit message, and the SHA. E.g.
        
	$ git log

## git status

This command displays any updates made in the three-tree architecture. It is highly adviseable to use this command every time a change has been made. I.e. added new file, committed a file, pushed a file etc.
  
Those of you who follow my blog, may have noticed that I uploaded the same image of the git architecture. This time, instead of focusing on each directory individually, we will focus on how directories interact with one another. Let’s start by taking you through you the workflow, in order to understand the practical applications of these commands.

## Pushing to GitHub

1. $ git add file.txt
   
   1. file.txt moves from working directory to staging 	index. Use `git status` command to check.

1. `$ git commit -m ‘initial commit’`
   
   1. file.txt moves from the staging index to the git repo.

1. `$ git push origin master`
   
   1. Uploads file from your local git repo to your 	GitHub repo.
=======
1. `$ git add file.txt`
   1. file.txt moves from working directory to staging index. Use the, `git status` command to check.
1. `$ git commit -m ‘type in a message to describe new changes applied to file’`
   1. file.txt moves from the staging index to the git repo.
1. `git push origin master`
   1. This command uploads the file from your local git repo to your GitHub repo.

## Pulling from GitHub


	$ git pull origin master
        
This command pulls from the GitHub repo into your working directory. From there your alterations are made to file. When complete, follow the git push instructions to upload the file back to your Git repo.
=======
This command pulls from the GitHub repo into your working directory. From there your alterations are made to file. When complete, follow the `git push` instructions to upload the file back to your Git repo.


There are a lot of technical commands in this piece. Let’s summarize what we have covered thus far: we learned some basic Git commands, when these commands should be utilized, a brief description of commands, how to push to git and GitHub, and how to pull from GitHub. All of these things are incredibly useful for any prospective programmer. Learn them, understand them, and most importantly don’t stop coding.