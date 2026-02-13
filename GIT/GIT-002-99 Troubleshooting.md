# Removing Error
![[Pasted image 20260213095712.png]]
- It says the file already modify and add in the staging area. It can seen as a protracting action.
3 Option can be done:
1. Mandatory remove the git.
```bash
git rm <filename>
``` 

2. I want not to be tracked, but the file need reserved.
```bash
git rm --cached <filename>
```

   3. I want cancel the staged status, then removed it
   ```bash
   git restore --staged <filename>
   git rm --cached <filename>
   ```