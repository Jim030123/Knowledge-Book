# Difference between GIT and VCS
Git storing data as changes to base version of each file![[Pasted image 20260129195918.png]]
- Git thinks of its data more like a series of snapshots of a miniature filesystem.
- Every time you commit or save the state of project, Git basically takes a picture of what all files look like at that moment and stores a reference to that snapshot.
- Efficiency
  If files have not changed. Git thinks about its data more like a stream of snapshots. 
Storing data as snapshot of the project over time![[Pasted image 20260129195929.png]]
- Git reconsider almost every aspect of [[GIT-001-1 Version Control (VC)|VC]] that most other systems copied from the previous generation.
- Git more like a mini filesystem with some incredibly powerful tools built on top of it, rather than simply a VCS.
# Characteristic
## Nearly Every Operation is Local

- Most operations in Git need only local files and resources to operate, generally no information is needed from another computer on network.
- Low network latency because have the entire history of the project right there on local disk, most operations seem almost instantaneous.
>[!note] Example: To browse the history of the project
>Git doesn't need to go out to the server to get the history and display, it simply reads it directly from local database. 
>
>This mean the project history almost instantly. If want to see the changes introduced between the current the current version of a file and the file a month ago,>
>
>Git can look up the file a month ago and do a local difference calculation, instead of having to either ask a remote server to do it or pull an older version of the file from the remote server to do it locally.
## Git Has Integrity
- Everything in Git is check summed before it is stored. It's impossible to change the contents of any file or directory without Git knowing about it.
- Can't lose information in transit or get file corruption without Git being able to detect it.
**SHA-1 hash**
- This id s 40-character string composed of hexadecimal characterises^[0-9 and a-f].
```bash
24b9da6552252987aa493b52f8696cd6d3b00373
```
## Git Generally Only Adds Data
- It is hard to get the system to do anything that is not undoable or to make it erase data in any way.
- We can experiment without the danger of severely screwing thing up.
## The 3 states
1. Modified
   That changed the file but have not committed it to database.
2. Staged
   That have  marked a modified file in its current version to go into next commit snapshot.
3. Committed
   That the data is safely stored in local database.

**Working tree, staging area and Git directory**![[Pasted image 20260129225504.png]]
- Working tree is a single checkout of 1 version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk to use or modify.
- Staging area is file, generally contained in Git directory, that stores information about what will go into next commit. Its technical name in Git parlance is the "index", but the phrase "staging area" works just as well.
- Git directory is where Git stores the metadata and object database of project. Copied when clone a repository from computer.
**Basic workflow goes something like this**
1. Modify files in working tree.
2. Selectively stage just those changes want to be part of next commit, which adds only those changes those changes to the staging area.
3. Do a commit, which takes the files as they are in the staging area and  stores that snapshot permanently to GIt directory.