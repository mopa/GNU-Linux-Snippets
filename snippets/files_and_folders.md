# Files and Folders Snippets


+ Show the first and last 5 lines of the syslog file, including a blank line between them.
```bash
(head -5; echo; tail -5) < /var/log/syslog
```

+ Random color per log line.
```bash
tail -F firewall.log |while read -r line;do printf "\033[38;5;%dm%s\033[0m\n" $(($RANDOM%255)) "$line";done 
```

+ A Tail of Two Files
```bash
sudo tail -F /var/log/syslog /var/log/auth.log 
```

+ I find brace expansion useful for renaming files. This cmd expands to "mv Picture.jpg Picture-of-my-dog.jpg"
```bash
mv Picture{,-of-my-dog}.jpg 
```

+ Just print the contents of a tar file instead of untarring it.
```bash
tar tvf potential_tar_bomb.tar 
```

+ Find those big files! ncdu is TUI program to generate and view usage statistics for disk space from the current directory and below. Use -x to avoid crossing filesystems and disable file modification with -r. ionice will give ncdu have less IO priority.
```bash
ionice ncdu -x -r 
```

+ Find files under the Documents directory larger than 500MiB , long list them with stats and sort based on the size column (-k7) numerically (n) and descending order (r = reverse), passing that output into less.
```bash
find Documents -size +500M -ls | sort -k7nr | less 
```

+ Search folders
```bash
find . -type d -iname 'docker*'
```

+ Print a count of the number of empty files under the current directory
```bash
find . -type f -empty | wc -l
```

+ This will run the ls command without using any alias called ls that might be set. You can do this with any real command. Another way to do this is with command ls.
```bash
\ls 
```

+ Compare the contents of 2 dirs. Show only 2 columns, each for files unique to the directory.
```bash
comm -3 <(ls dir1) <(ls dir2) 
```

+ List the 20 largest files and folders under the current working directory. On GNU based systems you can use the -h option to du and sort for human readableness. ncdu is also a nice TUI based option for this kind of thing.
```bash
du -ma | sort -nr | head -n 20 
```


+ Make a backup with date
```bash
sudo cp /etc/sudoers{,.backup_$(date +%Y%m%d)}
```

+ Sheesh! How many columns does this CSV file have anyways? For the first line, just print out the count of fields. Thanks awk.
```bash
awk -F, 'NR==1{print NF}' total_cases.csv 
```
