# Networking Snippets

+ What is my IP?
```bash
curl -silent -L http://checkip.amazonaws.com |tail -n 1
```

+ Scan your internal home network for hosts listening on TCP port 22 (SSH protocol).
```bash
nmap --open -p T:22 192.168.1.0/24 
```

+ Ping for internal home network.
```bash
nmap -sP 192.168.1.1-254
```

+ Scan the first 1000 ports for the especify IP
```bash
nmap -p -1000 192.168.1.1
```

+ List open ports and the app or service that use it
```bash
ss -tulpn

# In Real Time
watch ss -tulpn
```


+ Look through the last 9 compressed firewall log files in chronological order (reverse numerical by logrotate) and the current one for hits to port 8728 and generate daily hit stats.
```bash
zgrep -h DPT=8728 /var/log/firewall.{9..1}.gz /var/log/firewall | cut -c1-10 | uniq -c
```

+ Look at the rate of RDP requests to your host firewall logs for the year and summarize the hit count by day.
```bash
zgrep -h DPT=3389 firewall.log-2020*.gz | cut -c1-6 | uniq -c
```

+ Show all listening TCP/UDP ports for the current user. Or for everything if this is run as root.
```bash
lsof -Pan -i tcp -i udp 
```

+ Copy folders or files between servers o user to server.
```bash
tar -c source_folder/ | ssh user@192.168.1.250 'tar -xvf - -C /path/server/folder/'
```

+ Download an ISO image but rate limit the download to just 750KB/sec so it's not disrupting your parent's work video conferencing
```bash
wget --limit-rate=750k https://somenewlinux/.io/0.9alpha.iso
```

+ Look up the geographical location (by country) of an IP address that scanned your host.
```bash
geoiplookup 80.82.77.245 
```
