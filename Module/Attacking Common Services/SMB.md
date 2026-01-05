# Interacting
## GUI
### opening
![[Pasted image 20260106002512.png]]
## CMD
### listing contents
```
C:\htb> dir \\192.168.220.129\Finance\
```
### connecting
```
C:\htb> net use n: \\192.168.220.129\Finance
```
### connecting with credentials
```
C:\htb> net use n: \\192.168.220.129\Finance /user:plaintext Password123
```

### using commands on connected volume
```
C:\htb> dir n: /a-d /s /b | find /c ":\"
```

### searching for files with specific words
```
C:\htb>dir n:\*cred* /s /b

n:\Contracts\private\credentials.txt


C:\htb>dir n:\*secret* /s /b

n:\Contracts\private\secret.txt
```
Recommenden Words include
- cred
- password
- users
- secrets
- key
- Common File Extensions for source code such as: .cs, .c, .go, .java, .php, .asp, .aspx, .html.
### looking within files
```
c:\htb>findstr /s /i cred n:\*.*
```
## PS
### Listing Directory Contents
```
Get-ChildItem \\192.168.220.129\Finance\
```
