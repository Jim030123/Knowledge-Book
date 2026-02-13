- Should gave a bona fide Git repository on local machine and a checkout or working copy of all of its files in front of you. Start making changes and committing snapshots of those changes into repository each time the project reaches a state want to record.
- Each file in working directory can be in 1 of 2 states:
1. Tracked
   files that were in the last snapshot, as well as any newly staged files; they can be unmodified, modified or staged.
2. Untracked
   Any files in working directory that were not in last snapshot and are not in staging area. When clone a repository, all of files will tracked and unmodified because Git just checked them out and haven't edited anything.
**The Lifecycle of the status of files**![[Pasted image 20260208002149.png]]
# Git Status 
- Checking the status of files.
```bash
git status
```
![[Pasted image 20260208003131.png]]
- Have a clean working directory; in other words, none tracked files are modified.
- Git also doesn't see any untracked files, or they would be listed here.
- The command tells which branch on and informs that it has not diverged from the same branch on the server.
>[!info] Change default branch name mid-2020
>The default branch name in some newly created repositories is ***main*** and not ***master***.

# README
- File is untracked, because it's under the "Untracked files" heading in status output.
- Untracked, means that Git sees a file didn't have in the previous snapshot^[commit] and which hasn't yet been staged.
# Tracking New Files
- Can tell that it's staged because it's under the "Changes to be committed" heading. The version of the file at the time ran ***git add*** and what will be in subsequent historical snapshot.
```bash
git add <files>
```
- The command takes a path name for either a file or a directory.
- Function:
  - Tracking new Files
  - Stage File
  - Marking merge-conflicted files as resolved.
helpful to think of it more as "add"

```bash
git add README
git status
```

![[Pasted image 20260208235042.png]]
- Changed not staged for commit, which means that a file is tracked has been modified in the working directory but not yet staged.

# Staging Modified Files
![[Pasted image 20260209083804.png]]

- README.md us listed as both staged and upstaged. IT turns out that Git stages a file exactly as it is when run the ***git add***.
```bash
git add .
git status
```
![[Pasted image 20260209082508.png]]

## Short status
```bash
git status -s
```
```git
M READNE
A lib/git.rb
M lib/simplegot.rb
?? LICENSE.txt
```

| Note | Meaning                                            |
| ---- | -------------------------------------------------- |
| ??   | New files that aren't tracked                      |
| A    | New files that have been added to the staging area |
| M    | modified file                                      |
# Ignoring Files
- Gave a class of files that don't want Git to automatically add or even show as being untracked.
- Generally automatically generated files sync as log files or files produced by build system.
```bash
cat .gitignore
*.[oa]
*~*
```

| Lines | Meaning                                                                                                                             |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1     | Git to ignore any files ending in "o" or "a"<br>Object and achieve files that may be the product of building code.                  |
| 2     | Git to ignore all files whose names end with a tilde (-), which is used by many text editors such as Emacs to mark temporary files. |
## .gitignore files
- Blank lines or lines staring with ***#*** are ignored.
- Standard glob patterns work and will be applied recursively throughout the entire working tree.
- Can start patterns with a forward slash (/) to avoid resistivity.
- Can end patterns a forward slash (/) to specify a directory a directory.
- Can negate a pattern by staring it with an examination point (!).
An asterisk (\*) matches 
- zero or more characters 
- [abc] matches any character inside the brackets
- (?) marches a single character.
- ([0-9]) matches any character between them
Can also use 2 asterisks to match nested directories a/*\*/z would match
- a/z
- ab/z
- a/b/c/z
```
# ignore .a files
*.a

# but do track lib.a, even though ignpring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in an y files in any directory name build
/build

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in tge doc/ directory and any of its subdirectories
doc/**/*.pdf
```
# Git Diff
Most often to answer these 2 questions:
- What have changed but not yet staged?
- What have staged that are about to commit?
## What different between Git Status and Git Diff

| Git Status                                                       | Git Diff                                |
| ---------------------------------------------------------------- | --------------------------------------- |
| Answers those questions every generally by listing the file name | Shows the exact lines added abd removed |
![[Pasted image 20260209092423.png]]
- Important to note that ***git diff*** by itself doesn't show all changes made since last commit - only changes that are still upstaged.
- Staged all of changes, ***git diff*** will give no output.
## Git Cached / Git Staged
```bash
git diff --cahced
git diff --staged
```
![[Pasted image 20260209093641.png]]
# Committing Changes
- Commit message inline with the ***commit*** command by specifying it after a  -m flag.
```bash
# Message
git commit -m 
```

![[Pasted image 20260209093922.png]]
- Which branch committed (master).
- What SHA-1 checksum the commit has (463dc4f).
- How many files were changed
- Statistics about lines added and removed in the commit.
## Skipping the Staging Area
- Git provides a simple shortcut. Adding the ***-a*** option to the ***git commit*** command makes Git automatically stage every file that is already tracked before doing the commit.
```
git commit -a
```

>[!note] ***\-a*** flag includes all changed file
>This is convenient but be careful, sometimes this flag will cause to include unwanted changes.
## Removing Files
- To remove a file from Git, have to remove it from tracked files and then commit.
```bash
rm <filename>
```
- Removes the file from working directory, didn't see it as an untracked file the next time around
- Simply  remove the file from working directory, it shows up under the "Changes not staged for commit"^[unstaged]
![[Pasted image 20260213095152.png]]

```bash
git rm <filename>
```

![[Pasted image 20260213100747.png]]
- Next time commit, the file will be gone and no longer tracked. If modified the file had already added it to the staging area, must force the removal with the ***-f*** option. This is a safety feature to prevent accidental removal of data that hasn't yet been recorded in a snapshot and that can't be recovered from Git.
- To do keep the file in staging 