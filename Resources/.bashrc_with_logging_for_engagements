# ~/.bashrc: executed by bash(1) for non-login shells.

# Basic .bashrc file that has been slightly modified to log for offensive assessments. 
# If it isn't logged then it never happened.
# Author: Deviant

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
# Also unlimited history size because I am forgetful :D 
shopt -s histappend
HISTSIZE=
HISTFILESIZE=

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
#[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# Alias definitions.
# I did not add mine here because I did not want to break the workflow of someone dwloading these
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# Custom prompt
PS1='\[\e[0;95m\][\[\e[0;92m\]\d \[\e[0;95m\]\t\[\e[0;92m\]] \[\e[0;95m\]$(ip route get 1.1.1.1 | awk -F"src " '"'"'NR==1{split($2,a," ");print a[1]}'"'"') \[\e[0;92m\]\W \[\e[0;95m\]> \[\e[0m\]'

# Log history into a new file every time terminal is opened (make a .backup directory for this to work)
test "$(ps -ocommand= -p $PPID | awk '{print $1}')" == 'script' || (script -f $HOME/.backup/logs/$(date +"%d-%b-%y_%H-%M-%S")_shell.log)

# Set Terminal Title to User@Host > Directory
PROMPT_COMMAND='echo -en "\033]0;$(whoami)@$(hostname) >  $(pwd | cut -d "/" -f 4-100)\a"'
