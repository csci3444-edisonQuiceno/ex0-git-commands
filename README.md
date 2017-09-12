# ex0_git_commands
Example project to show using git commands at command line

## Make sure git is installed
git --version

## First see and set, git config settings
### To see all git config settings
git config --list

### To see specific global git config setting like user.name , user.email
git config --global user.name <br>
git config --global user.email

### To set user.name , user.email  global config setting (NOT needed if it had been set before, viewed above)
<pre>
git config --global user.name  'yourGithubUsername'
git config --global user.email 'yourGithubEmail@gmail.com'

git config http.sslVerify 
git config --global http.sslVerify 
git remote –v
</pre>

### if below is true , then git commit will do conversion(from windows to unix) of line endings of file being committed. If false it will not. In windows machine it is suggested to be set to true. In Mac false.
git config --global core.autocrlf  <br>
git config core.autocrlf

### you can set it to true globally as
git config --global core.autocrlf true

## Create a project dir
<pre>
mkdir -p /c/fdu/csci3444/projects/ex0_git_commands
cd /c/fdu/csci3444/projects/ex0_git_commands
ls -a
</pre>
## Create local git repo at the project's home directory
git init   <br>
ls -a

## Create some files and dir
<pre>
touch index.html
touch style.css
touch script.js
touch README.md
touch letGitIgnoreMe.txt
mkdir target
touch target/someDumFile.txt
</pre>

## see what git thinks about these files and dir (NOTE git sees all files and dirs as "Untracked files" displayed in red)
git status

## Create .gitignore file with below contents
```sh
# files to be ignored by git #
##############################
letGitIgnoreMe.txt

# directories to be ignored by git #
####################################
/target/

# local git repo to be ignored by git as well #
###############################################
.git/
```
## To add a file from "working"(normal) dir to git's staging(index)
git add README.md

## To undo (remove) adding a file to git's staging(index)
git rm --cached README.md

## To add all files from working dir to staging
git add .

## To commit staged files to local repository
git commit -m 'initial commit' README.md

## To re-add to staging and commit to local repo in 1 step of ALL files that were added to staging before they were modified again
<pre>
echo 'deleteMe' >> README.md
unix2dos README.txt
git commit -a -m 'commit after dummy edit'
</pre>

## To see difference between working tree and staging(index)
git diff

## To see difference between staging(index) and (local)repo
git diff --cached

## To see difference between working tree and repo
git diff HEAD

## To create branch
git branch hello

## To switch to a branch
git checkout hello     <br>
git checkout masterOA

## To see branches and the active one (the one with * next to it)
git branch

## To create a branch and switch to that branch together
git checkout -b fix123Branch

## Make some changes in branch and commit them to branch
<pre>
echo 'h1 { color:red;}' >> style.css; unix2dos style.css
git add style.css
git commit -m 'added h1 element style' style.css
</pre>

## To switch to master branch and merge changes from another branch to master
git checkout master <br>
git merge fix123Branch

## To delete branch
git branch -d fix123Branch

## To create a tag
git tag V0.1 

## To see remote repository settings
git remote -v

## To set remote repository to a github repo
git remote add origin https://github.com/fdu-csci3444/ex0-git-commands.git

## To push to remote repo (NOTE -u is --set-upstream , which sets current branch as the remote tracking branch of the branch you are pushing)
git push -u origin master

## To push and overwrite (-f --force) differences in remote (for example let's say remote repo was created with a default README.md in github)
git push -u -f origin master

## To push a localBranchName as a different remoteBranchName
git push -u origin localBranchName:remoteBranchName


