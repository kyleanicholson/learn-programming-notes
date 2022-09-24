**Git** is a version control system - an 'epic save button' for your files and directories. **Version Contro**l is any system that allows you to understand the history of a file and how it has progressed.

Git is a program that allows you to annotate the history of a system (or group) of files via commits, which are “snapshots” of the differences made to the system at a given point in time.

Git allows you to save and to restore to a previous **commit**, which could be considered a save state or similar to a system restore point in Windows. You can add comments to different commits to easily navigate through the different points in the history of your files.


Git enables you to review how your project grows and easily look at or restore file states from the past. 

If connected to the internet, you can use **push** your project to remote repositories such as **GitHub** or alternatives such as Bitbucket, Beanstalk, or GitLab for sharing and collaborating.

It's worth noting that Git and Github are not exactly the same thing - Git is the name of the program you use when you are creating local repositories. This is usually done either via Git GUI or Git Bash. Git Bash is the name for the command line interface (CLI) version of Git which is used by many programmers. This is where you can enter commands to create repositories, commit changes, create branches, and much more.

GitHub is the name of the remote storage facility that can receive 'pushes' to allow them to be accessed from other locations by other developers or by you on a different computer. Github takes that lovely commit history and hosts it online so that you can access it from any computer.

Common terms that are thrown around:
- **Commit**: A snapshot of a particular point in the history of a 
- **Branch**:  Git commit history is like a tree - the trunk can be compared to the "master" or "main branch". Multiple teams can be working on the same tree by creating branches that are later "merged" witht the master branch. 
	- When a branch is merged, it overrides the master branch. 
- **Pulling**: Bringing github files to a local machine
- **Pushing**: Sending git files to a remote repository (such as GitHub)
- **Pull request**: Github feature that allows a developer to explain changes their branch will make to the master branch. 
- **Repo/Repository**: Specific git-enabled folder that contains all files that are part of a project.

General process that is followed for git/github (when collaborating with others) looks like this: 
	1.  Create local branch
	2.  Write some commits within local branch
	3.  Push to Github
	4.  Create Pull Request explaining changes that branch contains
	5.  Merge to master
	6.  Pull down new master commits locally
	7.  Repeat