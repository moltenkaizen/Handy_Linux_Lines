# Linux_Handy_Commands
Notespace for handy linux commands I want to reference

#Find things
Search for pattern in certain filetypes
```
grep --include=\*.{txt,csv,odt,ods} -rnw 'directory' -e "pattern"
```

#File things
Sort passwd file by UID
```
sort -t":" -k 3 -n /etc/paswd
```
Extract only username from passwd file
```
cut -d":" -f1 /etc/passwd
```

Follow a file (handy for logs)
```
tail -F /var/log/something
```

#Shortcuts
Final argument of previous command executed
```
mkdir somedir
cd $_
```

Run previous command. Find number using history then !number
```
history | grep somethinginteresting
!243
```

Exit status
```
ls afile ; echo $?
afile
0
ls nofile ; echo $?
ls: cannot access 'nofile': No such file or directory
2
```


#Permissions
Change permissions on files to 644 and folders to 744
```
find . -type f | xargs chmod -v 644
find . -type d | xargs chmod -v 744
```

#Networking
What is listening. n = numeric, l = listening, p = programs, t = tcp, u = udp
```
netstat -nlp
```
Netcat to check port
```
nc -vvzn IP PORT
```

Ping scan without nmap on class C network
```
for ip in {1..254}; do ping -c 1 192.168.1.$ip | grep ttl ; done
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
#RPM Packages
list files in rpm
```
rpm -qpl package.rpm
```
Show scripts in rpm
```
rpm -qp --scripts package.rpm
```

#Download stuff
```
curl https://something.com/something.sh -O
wget --no-check-certificate https://something.com/something.sh
```

#SSH
Connect to bigserver on ssh port 1234 then forward port 80 on wildcat to my local port 9999. Point local brower to locahost:9999
```
sudo ssh -L9999:wildcat:80 alarm@bigserver.org -p 1234
```

#DD with pv and pigz
```
dd if=/dev/mmcblk0 | pv | pigz --fast > raspbian_pi.img
```
