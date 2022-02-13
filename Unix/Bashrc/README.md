# Bashrc
### Use contents (full / partial) of this file in your .bashrc

### When adding an item to history, delete itentical commands upstream
export HISTCONTROL=erasedups

### Save 10000 items in history
export HISTSIZE=10000

### Append history to ~\.bash_history when exiting shell
shopt -s histappend

export PS1="[\D{%H:%M}]\[\033[01;32m\]\u:\[\033[01;34m\]\W\[\033[00m\]\$ "
### Some other options for PS1
###### export PS1="[\t]\u \W\$ "
###### export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$"
###### export PS1="[\t]\[\033[01;32m\]\u:\[\033[01;34m\]\W\[\033[00m\]\$ "

### Color codes
black="\[\e[30m\]"
red="\[\e[31m\]"
green="\[\e[32m\]"
yellow="\[\e[33m\]"
blue="\[\e[34m\]"
magenta="\[\e[35m\]"
cyan="\[\e[36m\]"
white="\[\e[37m\]"
reset="\[\e[0m\]"

## Useful alias
### Move to the parent folder.
alias ..='cd ..;pwd'

### Move up two parent folders.
alias ...='cd ../..;pwd'

### Move up three parent folders.
alias ....='cd ../../..;pwd'

### Display the directory structure.
alias tree='tree --dirsfirst -F'

### Make a directory and all parent directories.
alias mkdir='mkdir -p -v'

### Calender aliases
alias jan='cal -m 01'
alias feb='cal -m 02'
alias mar='cal -m 03'
alias apr='cal -m 04'
alias may='cal -m 05'
alias jun='cal -m 06'
alias jul='cal -m 07'
alias aug='cal -m 08'
alias sep='cal -m 09'
alias oct='cal -m 10'
alias nov='cal -m 11'
alias dec='cal -m 12'

clear

### Commands below are from: https://www.freecodecamp.org/news/bashrc-customization-guide/
### Print system information at startup
printf "\n"
printf "   %s\n" "USER: $(echo $USER)"
printf "   %s\n" "DATE: $(date)"
printf "   %s\n" "UPTIME: $(uptime -p)"
printf "   %s\n" "HOSTNAME: $(hostname -f)"
printf "   %s\n" "KERNEL: $(uname -rms)"
printf "   %s\n" "CPU: $(grep -m 1 'model name' /proc/cpuinfo) <<>> CORES: $(grep -c 'model name' /proc/cpuinfo)"
printf "   %s\n" "MEMORY: $(free -h | awk '/Mem/{print "Used: "$3" / Total: "$2}')"
printf "\n"

### Set the prompt.
function git_branch() {
    if [ -d .git ] ; then
        printf "%s" "($(git branch 2> /dev/null | awk '/\*/{print $2}'))";
    fi
}

### Set the prompt (+ custom color).
function bash_prompt(){
    PS1='${debian_chroot:+($debian_chroot)}'${blu}'$(git_branch)'${pur}' \W'${grn}' \$ '${clr}
}