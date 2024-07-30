```
CURRENT_IP=$(ip addr | grep inet |grep -v "127.0.0.1" |grep -v inet6|awk '{print $2}'|awk -F "/" '{print $1}'| head -1)
```