# View all of settings and they are coming
![[Pasted image 20260207001202.png]]
# Set Identity
```bash
git config --global user.name "Jim Ng"
git config --global user.email "jimngyinggeemicky@gmail.com"
```
- Need to do this only once if pass the ***--global*** option, Git will always use that information for anything do on that system.
- Want to override this with a different name or email address, run the command without ***--global*** the option when you're in the project.
# Set Editor
```bash
# Linux Based
git config --global core.editor emacs

git config --global core.editor "'C:/Program Files/Notepad+/notepad++.exe' -multiInst -notabbar -nosession -noPlugin" 
```
- Vim, Emacs and Notepad++ are popular text editor often used by developers on Unix-based systems
# Set Default Branch Name
```bash
git config --global init.defaultBranch main
```
# Checking Setting
```bash
git config --list
```

## Check specific key's value
```bash
git config <key>
```