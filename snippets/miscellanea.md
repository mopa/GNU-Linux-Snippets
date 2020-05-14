# Miscellanea Snippets

egrep -o "(Donnie|Frank|Roberta|Grandma)" story.txt |sort|uniq -c|sort -nr 
# Search for names and build a frequency count for each name.

df . 
# This is an easy way to find out what partition the current directory is on, regardless of symlinks.

alias hideprev='history -d $((HISTCMD-2)) && history -d $((HISTCMD-1))' 
# Hide the previous command you just ran and forgot to use a prefix space to ignore it.

date --help | grep % 
#  Grep a list of all the date/time format sequences. I use this a lot when I'm programming.

paste <(cal 2020) <(cal 2021) 
#  Look at the full year calendar for 2020 and 2021 side by side. (Requires a term width >= 138). If you don't have that large of a term, you can change the orientation to vertical like this: { cal 2020 ; cal 2021; } or pipe it to less -S

exiftool -v '-Directory<DateTimeOriginal' -d %Y . 
#  *Move* photos in the current directory with EXIF data to directories according to the year created/taken and be verbose about it. This will automatically create the directories for you.
