In this piece I will be discussing 2 basic, yet essential commands in git, git push and git pull. Additionally, some basic terminology will be provided, for readers who are not as familiar with git. Furthermore, following each definition I will provide the git command which must be entered, in your terminal, in order to complete said task.


git push- This command allows you to share the commits you’ve made with other. i.e. it uploads files from your git repository to GitHub. Bear in mind that, this command will only push files that are  in your git repository. This command WILL NOT upload files from your staging index or your working directory.


        $ git push origin master


git pull- This is the mirror command of git push. Instead of uploading files from your git repo to GitHub, this command drags files from your GitHub repo to your local git repo.


        $ git pull origin master
        
Point of clarification: Your git repo is the repository on your local computer. This is 
where you will get most of your work done. Also, this is the final step in the three-tree 
architecture. GitHub, is a medium where files are viewed and shared. This is VERY important to understand No true developer works on files directly on GitHub. Don’t be a fucking amateur. Follow and internalize this process.


git add- This is the command used to add files from your working directory to your staging 
index. By adding a file to your staging directory, git beings tracking it. In contrast, files 
which are in your working directory are untracked. Once your file is ready to go, use 
this command to add it to the staging area.


add all files: $ git add .
add specific files: $ git add ‘file.txt’


git commit- Once your file is in the staging area and you are satisfied with your alterations, 
commit your changes to the git repo. Git records your name, email address, time and 
date of commit, and the commit message with ever commit you make. The commit 
message should contain information about the changes made to the file. i.e. If I 
changed an HTML file, by adding a new head, and an ordered list nested inside of that 
head, then my commit message should read as follows:
        git commit -m ‘added head. ordered list nested inside of head’
In conclusion, a perfect commit message should be clear and brief. Do not say write 
anything you don’t have to.


$ git commit -m ‘type commit message’


git log- This commands provides the user with an in-depth list of commits, pertaining to that specific file. The list of commit messages are displayed starting with the new commits on the top. Inside the commit, you will find the following: author, date, commit message, and the SHA.
        $ git log


git status-  This command is used to see if anything has been altered or staged since the last 
commit. I HIGHLY advise you to use this command every time something has 
changed. (i.e. added new file, committed a file, pushed a file etc.). This command will 
let you know where you are in the three-tree architecture; this way you do not get lost.
  



























Those of you who follow my blog posts may have noticed that I uploaded the same image as last time, the git architecture. However, instead of focusing on each directory individually, we will focus on how each directory interacts with the other. This involves taking you through the git workflow.


Pushing to GitHub
        Assuming your file.txt is in your working directory. Here is a list of commands to upload 
to GitHub
1. $ git status
   1. In order to see if any files are untracked. Let’s assume that file.txt is an untracked file in our working directory. 
1. $ git add file.txt
   1. file.txt moves from working directory to staging index. Use git status command to ensure this is true.
1. $ git commit -m ‘type in a message to describe new changes applied to file’
   1. file.txt moves from the staging index to the git repo.
1. git push origin master
   1. This command uploads the file from your local git repository to your GitHub repo.


Pulling from GitHub
1. $ git pull origin master
        
This command will pull from our GitHub repo to your working directory. From there you 
can make any alterations to your file. Once you have made the necessary alterations, 
following the git push instructions to upload the file to your git repo; then push the file 
to GitHub.


This was definitely the densest blog piece I have written thus far (It also took me much longer to write). There are a lot of technical commands in this piece. Let’s summarize what we have covered thus far: we learned some basic Git commands, when these commands should be utilized, a brief description of commands, how to push to git and GitHub, and how to pull from GitHub. All of these things are incredibly useful for any prospective programmer. Learn them, understand them, and most importantly don’t stop coding.