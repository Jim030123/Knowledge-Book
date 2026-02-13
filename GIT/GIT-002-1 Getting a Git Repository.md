- Obtain a Git repository in 1 of 2 ways:
	- Can take a local directory that is currently not under VC and turn it into a Git repository.
	- Can clone an existing from elsewhere.
# Initializing a Repository in an Existing Directory
## Linux
```bash
cd /home/user/my_project
```
## macOS
```bash
cd /Users/user/my_project
```
## Windows
```bash
cd C:/Users/user/my_project
```
# Git Init 
- This creates a subdirectory named ***.git*** that contains all of necessary repository files.
- Want to start VC existing files, should probably begin tracking those files and to an initial commit.
# Git Add & Git Commit
- Can accomplish that with a few ***git add*** command that specify the files want to track ***git commit***.
```bash
git add ~.c
git add LICENSE
git commit -m "Initial project version"
```
# Git Clone
- Want to get a copy of existing Git repository.
- This is an important distinction - instead of getting just a working copy, Git receives a full copy of nearly all data that the server has.
```bash
git clone <url>
```
- That creates a directory named ***libgit2***, initialized a .git directory inside it, pulls down all the data for that repository and checks out a working copy of the latest version.
```bash
git clone https://github.com/libgit2/libgit2
```
- Want to clone the repository into a directory named something other than ***libgit2***, can specify the new directory name as an additional argument.
- That command does the same thing as previous one, but the target directory - ***mylibgit***
```bash
git clone https://github.com/libgit2/libgit2 mylibgit
```
