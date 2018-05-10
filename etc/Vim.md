# Vim



## Environment Variables

- USER : username `echo $USER`
- PS1 : prompt
- PATH : executable paths
- EDITOR : default editor
- TERM : terminal
- more...

### .bash_profile

- includes configuration code for your terminal
- `touch .bash_profile`: to create .bash_profile.
- `source ~/.bash_profile` : evaluate (run) .bash_profile



## Vim editor

- `vim` : starts a vim
- `vim file.txt`: opens a file.txt in vim
- Modes: NORMAL(esc), INSERT(i, o), COMMAND(:), VISUAL



## Vim shortcuts (NORMAL)

- naviagation (h,j,k,l), { (previous white space), } (next white space)
- d (delete): dd(line), d2w, dw, etc
- u (undo)
- :q! (quit without saving), :w (save), :wq (save and quit)







## My Bash profile

```bash
Last login: Wed May  9 15:07:16 on ttys000
-bash: alias: -=: invalid option
alias: usage: alias [-p] [name[=value] ... ]
(jin-tak.han)[ ~ ] $ bp

  1 
  2 # Prompt
  3 # -----------------------------------------------------------------
  4 export PS1="(\[\033[1;32m\]\u\[\033[0m\])[\[\033[1;34m\] \W \[\033[0m\]] \[\    033[1;31m\]\$\[\033[0m\] "
  5 
  6 
  7 # Alias
  8 # -----------------------------------------------------------------
  9 alias -='cd -'
 10 alias ..='cd ..'
 11 alias c='clear'
 12 alias bp='vim ~/.bash_profile'
 13 alias reload='source ~/.bash_profile'
 14 alias desktop='cd /Users/jin-tak.han/Desktop'
 15 
 16 
~                                                                               
                                                                         
"~/.bash_profile" 16L, 425C

```



