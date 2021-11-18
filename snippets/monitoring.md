# Monitoring Snippets

+ To know the time it takes to execute a process
```bash
ps -eo pid,etime,comm | grep firefox
```

+ Change the output of ps to be just memory, pid and process args, sorting the processes by memory usage (first column) and cutting the lines to fit the terminal.
```bash
ps -e -orss=,pid=,args= | sort -b -k1n | cut -c1-$COLUMNS 
```

+ View the current battery charge of a mouse
```bash
upower -i $(upower -e | grep 'mouse')
```
