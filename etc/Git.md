# Git



## Cheat sheet

- https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf







## Cheat ignore

1. In Terminal, navigate to the location of your Git repository.
2. Enter `touch .gitignore` to create a *.gitignore* file.

3. how to edit

   That can be done using the vim editor. Simply type `vi [path-to-file]\file` and you will open the vim terminal editor. There's a lot (like a LOT) you can do with vim, but for your purposes:

- Press `a` to toggle the edit mode
- Edit stuff
- Press `Esc` to finish edit mode and toggle the command mode
- Press/type `:` to indicate you want to type a command
- Type and enter `wq` to save the changes and exit



4. sample

```java
# Compiled source #
###################
*.com
*.class
*.dll
*.exe
*.o
*.so

# Packages #
############
# it's better to unpack these files and commit the raw source
# git has its own built in compression methods
*.7z
*.dmg
*.gz
*.iso
*.jar
*.rar
*.tar
*.zip

# Logs and databases #
######################
*.log
*.sql
*.sqlite

# OS generated files #
######################
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db
```





If you already have a file checked in, Git will not ignore the file if you add a rule later. You must untrack the file first, by running the following command in your terminal: 

**git rm --cached FILENAME**

**git commit -m "Any message"**



