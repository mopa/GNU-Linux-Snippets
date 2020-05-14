# Networking Snippets

nmap --open -p T:22 192.168.1.0/24 
# Scan your internal home network for hosts listening on TCP port 22 (SSH protocol).

nmap -p -1000 192.168.1.1
# Scan the first 1000 ports for the especify IP

zgrep -h DPT=8728 /var/log/firewall.{9..1}.gz /var/log/firewall | cut -c1-10 | uniq -c
#  Look through the last 9 compressed firewall log files in chronological order (reverse numerical by logrotate) and the current one for hits to port 8728 and generate daily hit stats.

lsof -Pan -i tcp -i udp 
#  Show all listening TCP/UDP ports for the current user. Or for everything if this is run as root.

tar -c source_folder/ | ssh user@192.168.1.250 'tar -xvf - -C /path/server/folder/'
# Copy folders or files between servers o user to server.
