# Files and Folders Snippets


Show the first and last 5 lines of the syslog file, including a blank line between them.
```bash
(head -5; echo; tail -5) < /var/log/syslog
```

tail -F firewall.log |while read -r line;do printf "\033[38;5;%dm%s\033[0m\n" $(($RANDOM%255)) "$line";done 
# Random color per log line.

sudo tail -F /var/log/syslog /var/log/auth.log 
# A Tail of Two Files

mv Picture{,-of-my-dog}.jpg 
# I find brace expansion useful for renaming files. This cmd expands to "mv Picture.jpg Picture-of-my-dog.jpg"

tar tvf potential_tar_bomb.tar 
# Just print the contents of a tar file instead of untarring it.

ionice ncdu -x -r 
# Find those big files! ncdu is TUI program to generate and view usage statistics for disk space from the current directory and below. Use -x to avoid crossing filesystems and disable file modification with -r. ionice will give ncdu have less IO priority.

find Documents -size +500M -ls | sort -k7nr | less 
#  Find files under the Documents directory larger than 500MiB , long list them with stats and sort based on the size column (-k7) numerically (n) and descending order (r = reverse), passing that output into less.

\ls 
#  This will run the ls command without using any alias called ls that might be set. You can do this with any real command. Another way to do this is with command ls.

comm -3 <(ls dir1) <(ls dir2) 
#  Compare the contents of 2 dirs. Show only 2 columns, each for files unique to the directory.

du -ma | sort -nr | head -n 20 
#  List the 20 largest files and folders under the current working directory. On GNU based systems you can use the -h option to du and sort for human readableness. ncdu is also a nice TUI based option for this kind of thing.

find . -type d -iname 'docker*'
# Search folders

sudo cp /etc/sudoers{,.backup_$(date +%Y%m%d)}
# Make a backup with date