Create a new repo from the command line (SSH method)
```shell
git init # create the repo
git add README.md # add a readme if desired
git commit -m "first commit" #creates the commit
git branch -M main # sets the branch to main
git remote add origin git@github.com:[enter the full SSH here] 
git push -u origin main #push current commit to github repo
```

Push an existing repo from the command line
```shell
git remote add origin git@github.com:kyleanicholson/learn-programming-notes.git
git branch -M main
git push -u origin main
```