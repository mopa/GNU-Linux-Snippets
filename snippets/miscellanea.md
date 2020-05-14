# Miscellanea Snippets

Search for names and build a frequency count for each name.
```bash
egrep -o "(Donnie|Frank|Roberta|Grandma)" story.txt |sort|uniq -c|sort -nr 
```

This is an easy way to find out what partition the current directory is on, regardless of symlinks.
```bash
df . 
```

Hide the previous command you just ran and forgot to use a prefix space to ignore it.
```bash
alias hideprev='history -d $((HISTCMD-2)) && history -d $((HISTCMD-1))' 
```

Grep a list of all the date/time format sequences. I use this a lot when I'm programming.
```bash
date --help | grep % 
```

Look at the full year calendar for 2020 and 2021 side by side. (Requires a term width >= 138). If you don't have that large of a term, you can change the orientation to vertical like this: { cal 2020 ; cal 2021; } or pipe it to less -S
```bash
paste <(cal 2020) <(cal 2021) 
```

*Move* photos in the current directory with EXIF data to directories according to the year created/taken and be verbose about it. This will automatically create the directories for you.
```bash
exiftool -v '-Directory<DateTimeOriginal' -d %Y . 
```
