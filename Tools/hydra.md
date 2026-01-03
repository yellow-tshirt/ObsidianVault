# Ein Benutzer viele Passwörter
```
hydra -l username -P password.list <service>://<ip>
```
# Viele Benutzer ein Passworter
```
hydra -L user.list -p password <service>://<ip>
```
# Viele Benutzer viele Passwörter
```
hydra -L user.list -P password.list <service>://<ip>
```