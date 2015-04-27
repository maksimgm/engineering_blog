## What is a branch?

A branch is an independent line of development, separate from the master branch.

####**List of branch commands**

*Display current branch*

	$ git branch
	
*Compare branches*

	$ git diff master..other_branch

*Create a new branch*
	
	$	git branch 'new_branch'

*Switch branches*

	$ git checkout 'branch_name'
	
	Make sure your Working Directory is clean, before switching branches.
	
*Create and switch into a new branch, simultaneously*
	
	$ git checkout -b 'new_branch'
	
*Rename a branches*

	$ git branch -m 'branch_1'

*Delete a branches*

	$ git branch -d 'new_branch'

## Why are branches vital?

Branches are cheap-- they are easy to create and delete; which makes them easy to work with. They are a powerful feature on git, because they allow you to collaborate on projects without making unnecessary changes to the Master branch. 

Furthermore, collaborators can view your changes, makes comments, and commit additional changes to the branch. Once the work is finished, the branch is merged with master.

## What is merging?

According to [git-scm.com](http://git-scm.com/docs/git-merge), merging joins two or more development histories together.

**The Master branch should contain finished material.**


## How to merge changes to master?

1. Checkout the branch that is receiving changes
2. If in master branch, and want to merge file_one, e.g.:

		$ git merge file_one
		
	Merges can get complicated. To avoid 	complications, run `$ git merge` with a clean **Working Directory**.

## Merge Conflicts

According to [git-scm](http://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging), If you changed the same part of the same file differently in the two branches you're merging together, Git won't be able to merge them properly. As a result, you'll get a merge conflict that looks like this:

	$ git merge new_file
	Auto-merging index.html
	CONFLICT (conflict): Merge conflicts in index.html
	Automatic merge failed; fix conflicts and then commit the results.

## Resolving Merge Conflicts

1. Abort Merge (easiest)
	
	* `$ git merge --abort`
	
2. Resolve the Conflict Manually (common)

	* `$ git status`
	* open file and resolve changes.
	* add file
	* commit changes
	* `$ git merge file_name` 
	
3. Use Merge Tool
	* `$ git merge tool`
	
	* This method helps you resolve merge conflicts, but manual editing may be required afterwards. The downside is, you become too confortable with this command, and lack the appropriate knowledge necessary to resove merge conflicts manually.

#### Understanding Merge Conflict Syntax

Git will makes changes to your file, in order to show you where the conflict occured. [Stack Overflow](http://stackoverflow.com/questions/9207260/merge-conflict-resolution), provides a guide for reading git merge syntax:

1. The part between `<<<<<<` and `======` comes fromt the `HEAD` revision, which is the committed state prior to the merge operation.
2. The part between `======` and `>>>>>>` comes from the verion being merged.
3. The part after the `>>>>>>` is the comment of the commit that introduced the conflicting change.

## Strategies to Reduce Merge Conflicts

1. Keep commits small and focused.
2. **Beware** of stray edits to whitespace e.g.

	* spaces
	* tabs
	* lines


3. Merge often.
4. Track changes to master often. 
5. Make sure branches stay in sync with master.