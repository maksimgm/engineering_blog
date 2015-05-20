The Git Workflow
==================

## Overview

By now, you should have a solid understanding of git commands, git architecture, and the difference between git and GitHub. It is time to put all of this together, by going through the git workflow.

Imagine, you are at work and your manager wants you to make changes to a repository on GitHub called, *cookies*. Below, are step-by-step instructions on how to do just that.

### Step 1

Once you've located the repository on GitHub, clone it to your local machine. e.g.

	$ git clone <remote repository URL>
	
This command will clone the repo onto your local machine.

### Step 2

Now that we have a copy of the *cookies* repo, we will create a branch called, *sidebar*. e.g.

	$ git checkout -b sidebar
	
Branches are created in order to make changes to files without merging those changes into **Master** branch. Changes should only be merged into **Master** branch once they have been reviewed and approved by a senior developer.

Once you're satisfied with your changes, move the file from the **Working Directory** to the **Staging Index** e.g.

	$ git add snickerdoodle.html
	
	Note: snickerdoodle.html is a file, in our sidebar branch, in the cookies repository.
	
### Step 3

Move *snickerdoodle.html*, from the **Staging Index** to the **Git Repository**, on your local machine. e.g.
	
	$ git commit -m "commit message"
	
### Step 4

Now that *snickerdoodle.html* is in **Git Repository**, we will push the changes to *sidebar branch*,  in the *cookies repo* on GitHub.

	$ git push origin sidebar
	
### Step 5 

When your work is ready to be merged into the **Master** branch, issue a pull request. This is not the same as the  `$ git pull`. So, what is a pull request?

According to [OSSWATCH](http://oss-watch.ac.uk/resources/pullrequest), a pull request occurs when a developer requests for changes committed to an external repo to be considered for inclusion in a project's main repo.

### Performing a Pull Request

1. Navigate to the repo on GitHub. 
2. On the left side of the page you will see a green button with two arrows. Click on it. 
3. Make sure your base is **Master** and compare is **sidebar**. Click _create pull request_
4. Enter the title of the request and leave a comment. Make sure to tag the people who you'd like to be notified of the pull request using , _@_ followed by their GitHub username.

### Conclusion

This information sounds confusing at first. However, if you follow the steps provided, you will have no problem getting through the git workflow. Remember, the point of pull requests is to formalize the collaborative process, and allow other decelopers to review your code before it is merged into **Master**. Since line comments are available in pull requests, developers can have a conversation about the code, then make changes, in light of such converations, commiit new solutions, then discuss those as well.