# Linux_Handy_Commands
Notespace for handy linux commands I want to reference

#Find things
Search for pattern in certain filetypes
```
grep --include=\*.{txt,csv,odt,ods} -rnw 'directory' -e "pattern"
```

#Text File Processing
Sort:
-sort passwd file by UID-
```
sort -t":" -k 3 -n /etc/paswd
```
#Permissions
Change permissions on files to 644 and folders to 744
```
find . -type f | xargs chmod -v 644
find . -type d | xargs chmod -v 744
```

#Networking
-what is listening-
```
netstat -tnlp
```
-netcat to check port-
```
nc -vvzn IP PORT
```
