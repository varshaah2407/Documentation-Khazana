# Git and GitHub Documentation
## Git
Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
## GitHub
While git is a service system, GitHub is one of the platforms which provide this service online. GitHub allows you to host your repositories online.
## Git Commands

### Creating a git repository 
- ```git init``` -> To initialise git repository in the present directory.
- ```git status``` -> Tells you about the untracked changes and staged changes in the repository.
					<br> &emsp; Red text is for untracked files whereas Green text is for staged files.

### Staging file/files of the repository
- ```git add filename``` -> To add the file with changes to the staging area.
					<br> &emsp; git add . -> To add all the unstaged files to staging area.

- ```git rm --cached filename.txt``` -> Unstages the file.

### Comitting files

- ```git commit -m "Message" ``` -> To commit the stagged changes. In other words to make a checkpoint/save-point of the repository state.

- ```git commit -a -m "Message" ``` -> SKIPS the Staging part and directly COMMITS

- ```git restore --staged filename ``` -> To remove the file from the staging area without committing it.

- ```git commit --ammend ``` -> To ammend the previous commit.

- ```git log``` -> Shows the history and hash of all the commits that were made.

- ```git diff``` -> LOGS the changes.

- ```git log --oneline``` -> Shows the history and hash of all the commits that were made, in a single line.

- ```git reset hash_of_the_commit``` -> Removes all the log of commit above the commit whose hash is mentioned.
					<br> &emsp; After git reset the files that were modified in the removed commits are now in the unstagged area or basically are currently untracked.

- ```git reset --hard hash_of_the_commit``` -> Removes all the file changes and leaves nothing untracked or unstaged.

- ```git restore filename``` -> brings back the files which were removed in git reset.
					<br> &emsp; the files lost in git reset can also be kept in the stash area.
					<br> &emsp; Stash is similar to a backstage area.

- ```git stash``` -> This removes the file from your directory and stashes it without commiting.
					<br> &emsp; In other words moves the file from your directory to a temporary waiting area / stash area(or backstage).

#### &emsp; &emsp; Note: In order to stash some file, you need to bring the file first to the staging area by git add filename and then stash them.

- ```git stash pop``` -> Brings the changed files from the stash area to the unstaged area.
					<br> &emsp; It brings the files from stash to your directory.

- ```git stash clear``` -> Removes the files from stash area and deletes them forever.

- ```git remote add origin url``` -> To connnect the remote repository (say on your GitHub profile) url to the local repository.
					<br> &emsp; Here origin is set as the name of that url.
					<br> &emsp; By convention all the repositories in your personal account have a url name as origin.

- ```git remote -v ```-> Shows all the urls attached to that local repository.

- ```git push origin master``` -> To push the changes to the origin url's master branch.
					<br> &emsp; Origin is the name of the url of our github repository.
					<br> &emsp; Master is the branch name of the repository.
					<br> &emsp; In modern versions the master branch is also called main branch, so do consider that as well.

### Git branching

- ```git branch``` -> LOGS all the branches of the Working Repository with an * in the Current Head.

- ```git branch newbranchname``` -> Creates a new branch.

- ```git checkout branchname``` -> Points the head to the branchname which is specified.
					<br> &emsp; Head is a pointer that points to the branch on which the commits will be added

- ```git switch branchname``` -> SWITCHES the Branch from one to another or CHANGING HEAD, but the current changes need to be STASHED or COMMITED.

- ```git switch -c newbranch OR git checkout -b newbranch``` -> CREATES a new branch and then SWITCHES to the branch.

- ```git branch -D newbranch``` -> Deletes newbranch, but you cant be headed on the branch you want to delete.

- ```git branch -M finalbranch``` -> Changes the name of the Branch you are Headed on.

- ```git remote add upstream url``` -> Adds the url as the upstream url.
					<br> &emsp; The source from which we have forked is called the upstream url and origin is the url of the repository which is in your personal github account.
- ```git pull``` -> To pull/fetch the changes from the original online repository (or the source of fork) to the local repository.

- ```git pull upstream main``` -> pulls data and commits from the upstream to your local repositories main branch
#### &emsp; &emsp; Note: In this case only the local is updated, your online forked repository is still not updated, to update it use ```git push origin main```.

- ```git rebase -i hash_of_commit_whose_upper_commits_need_to_be_squashed``` -> -i is for interactive mode.
					<br> &emsp; This will open an interactive screeen where you can change pick to s, for squashing that commit into the commit above it which is pick.

### Merging Branches
#### Fast Forward Merge (NO CHANGES done on the Master Branch)
Step 1:
- ```git switch master``` -> SWITCH the HEAD first to the first branch.

Step 2:
- ```git merge newbranch``` -> MERGES newbranch into master with HEAD on master.

#### Without merge conflicts
Step 1:
- ```git switch master``` 

Step 2:
- ```git merge -m "mergering message"``` -> CREATES a new commit unlike fastforwarding merges.

#### Merge conflicts (only if conflict message occurs)
	STEP 1:         OPEN UP files having merge conflicts 

	STEP 2:         REMOVE the conflicts 

		OPTION 1:           ACCEPT INCOMING CHANGES

		OPTION 2:           ACCEPT CURRENT CHANGES

		OPTION 3:           ACCEPT BOTH CHANGES

		OPTION 4:           COMPARE CHANGES 

	STEP 3:         REMOVE the conflict markers

	STEP 4:         STAGE and COMMIT the changes

#### Abort Merge (UNDO merge when mistakenly code merged & multiple unresolvable merging conflicts occur)
- ```git merge --abort```


### Everything about gitignore 
Git doesn't consider the files/folders which are in .gitignore 
	STEP 1:             create a .gitignore file

	STEP 2:             add files or folders inside the file to ignore, now the files are are untracked by github and wont be staged or commited


### Extras 
If a branch has been used to create a pull request then whatever changes you commit on that branch gets added to that pull request.
In other words, one branch can have one pull request only.
That is why it is advised to create a new branch for every feature or bug that you are working on.
So that you can open different pull requests for different features in the same project and the code base stays more organized and create pull request from that specific branch of your fork to the main branch of the original project.
