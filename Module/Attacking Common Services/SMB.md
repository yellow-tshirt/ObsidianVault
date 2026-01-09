# Interacting Windows
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

## mounting with New-PSDrive
```
PS C:\htb> New-PSDrive -Name "N" -Root "\\192.168.220.129\Finance" -PSProvider "FileSystem"
```

## new ps drive with credential
```
PS C:\htb> $username = 'plaintext'
PS C:\htb> $password = 'Password123'
PS C:\htb> $secpassword = ConvertTo-SecureString $password -AsPlainText -Force
PS C:\htb> $cred = New-Object System.Management.Automation.PSCredential $username, $secpassword
PS C:\htb> New-PSDrive -Name "N" -Root "\\192.168.220.129\Finance" -PSProvider "FileSystem" -Credential $cred
```

## Searching for file with specific substring
```
PS C:\htb> Get-ChildItem -Recurse -Path N:\ -Include *cred* -File
```

## searching in files
```powershell-session
PS C:\htb> Get-ChildItem -Recurse -Path N:\ | Select-String "cred" -List
```

# Interacting on Linux
## mounting a mb share
```shell-session
nchiato@htb[/htb]$ sudo mkdir /mnt/Finance
nchiato@htb[/htb]$ sudo mount -t cifs -o username=plaintext,password=Password123,domain=. //192.168.220.129/Finance /mnt/Finance
```

Or with credential file 
credfile
```
username=plaintext
password=Password123
domain=.
```

```
nchiato@htb[/htb]$ mount -t cifs //192.168.220.129/Finance /mnt/Finance -o credentials=/path/credentialfile
```