# What is VC
- A system that records changes to a file or set of files over time so that you can recall specific version later.
- Graphic or web designer and designer and want to keep every version of an image or layout. ^[VC system is a very wise thing to use]
- It allows to revert selected files back to a previous state, revert the entire project back to previous state, compare change over time, see who last modified^[Might be causing a problem, introduced an issue and when].
# Why not easy for VC method to copy files into another directory
- It is so simple, but it is also incredibly error prone.
- It is easy to forget which directory and accidentally write to the wrong file or copy over files.
>[!note] Example
>Programmers long ago developed local VCS that had a simple database that kept all the changes to files under revision control.

![[Pasted image 20260128122616.png]]
- [[GIT-001-2 Revision Control System (RCS)|RCS]] works by keeping patch sets in a special format on disk, it can then re-create what any file locked like at any point in time by adding up all the patches.
## Centralized VCS
- These versioned files and a number of clients that check out files from that central place.![[Pasted image 20260128125151.png| d]]
### Advantages
- Administrators have fine-grained control over who can do what, and it's far easier to administer a centralized VCS than it is to deal with local databases on every client.
### Disadvantages
- This setup also have some serious downsides. Most obvious is the single point of failure that the centralized server represents.
>[!note] Situation: server goes down for an hour
>- Nobody can collaborate at all or save versioned change to anything they're working on.
>- Hard disk, the central database is on becomes corrupted and backups haven't been kept, may lose absolutely everything.
>- Entire history of the project except whatever single snapshots people happen to have on their local machines.

## Distributed VCS
![[Pasted image 20260128133728.png]]
- If any server dies, these systems were collaborating via that server, any of the client repositories can be copied back up to the server to restore it.
- Every clone is really a full backup of all the data.
- Many of these systems deal pretty well with having several remote repositories they can work with, can collaborate with different group of people in different simultaneously within the same project. Allows it set up several types of workflow aren't possible in centralized systems^[Hierarchical models].
