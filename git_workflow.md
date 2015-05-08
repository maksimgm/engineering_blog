The Git Workflow
==================

## Overview

By now, you should have a good understanding of git commands, git architecture, and the difference between git and GitHub. It is time to put all of this together by taking you through the git workflow.


### Step 1

Your manager wants you to make changes to a repository on GitHub called, *Cookies*. Here are instruction on how to do that.
Once you find the repository on GitHub, clone it to your local machine. e.g.

	$ git clone <remote repository URL>
	
This command will clone the repo from GitHub onto your local git repo.

### Step 2

Now that we have a copy of the *cookies* repo, we will create a branch called, *sidebar*. e.g.

	$ git checkout -b sidebar
	
Branches are created in order to make changes to a file without merging it with the **Master** branch. Changes should only be merged into the **Master** branch once they are final.

Once you're satisfied with the changes you've made, move the file from the **Working Directory** to the **Staging Index** e.g.

	$ git add cake.html
	
	Note: cake.html is a file, in our sidebar branch, in the cookies repository.
	
### Step 3

Move cake.html, from the **Staging Index** to the **Git Repository**, on your local machine. e.g.
	
	$ git commit -m "initial commit"
	
### Step 4

Now that we have cake.html in our **Git Repository**, we will push the changes to our *sidebar branch*,  in the the *cookies repo* on GitHub.

	$ git push origin sidebar
	
### Step 5 

Once you feel your work is ready to be merged into the **Master** branch, you issue a pull request. This is not the same as the  `$ git pull` . So, what is a pull request?

According to [OSSWATCH](http://oss-watch.ac.uk/resources/pullrequest), a pull request occurs when a developer requests for changes committed to an external repo to be considered for inclusion in a project's main repo.

### Performing a Pull Request

1. Go to the page witht he GitHub repo. On the left side of the page you will see a green button with two arrows. Click on it. **insert screenshot**
2. Make sure your base is **Master** and compare is **sidebar**. Click _create pull request_
3. Enter the title of the request and leave a comment. Make sure to tag the individual who will approve the pull request using , _@_ followed by their GitHub username.

### Conclusion

All this information can sound difficult and complex. However, if you follow that instuctions I have provided, you should have no problem going through the git workflow.