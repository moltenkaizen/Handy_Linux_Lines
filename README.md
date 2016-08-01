# Linux_Handy_Commands
Notespace for handy linux commands I want to reference

#Find things
Search for pattern in certain filetypes
```
grep --include=\*.{txt,csv,odt,ods} -rnw 'directory' -e "pattern"
```

#File things
Sort:
-sort passwd file by UID-
```
sort -t":" -k 3 -n /etc/paswd
```
-extract only username from passwd file-
```
cut -d":" -f1 /etc/passwd
```

-Follow a file (handy for logs)
```
tail -F /var/log/something
```

#Permissions
Change permissions on files to 644 and folders to 744
```
find . -type f | xargs chmod -v 644
find . -type d | xargs chmod -v 744
```

#Networking
What is listening
```
netstat -tnlp
```
Netcat to check port
```
nc -vvzn IP PORT
```

Ping scan without nmap on class C network
```
for ip in {1..254}; do ping -W 100 -c 1 192.168.1.$ip | grep ttl ; done
```


#Systemd
-Reload systemd daemon. After editing service-
```
systemctl daemon-reload
```
-Show failed services-
```
systemctl --failed
```
-Show logs for ssh-
```
journalctl -u sshd --since today
```
-Error logs-
```
journalctl -p err
```
-follow logs-
```
journalctl -f
```
