# passwordless access
```
ssh-keygen -t rsa
cat .ssh/id_rsa.pub | ssh [user]@[host] 'mkdir -p .ssh; cat >> .ssh/authorized_keys'
```
