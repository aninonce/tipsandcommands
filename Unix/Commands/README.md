# Unix Commands

### Largest top {n} files in a directory, replace {n} by number
du -h -x -s -- <path to directory>/* | sort -r -h | head -{n}

### Check top commands {n} commands, replace {n} by number
history | awk '{cmd[$2]++} END {for(e in cmd) {print cmd[e] " " e}}' | sort -n -r | head -{n}