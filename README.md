# model_monitoring

# Watch model metrics from server over SSH

## on server
send logs to localhost:6006 with tensorboard

```
tensorboard --logdir="your_log_place" --host=localhost --port=6006
```


## on local machine

add this text to /.ssh/config
```
Host tensorboard-server
HostName "server_ip_address"
User "your_username"
LocalForward 6007 localhost:6006
IdentityFile "your_ssh_key"
IdentitiesOnly yes
ServerAliveInterval 60
ServerAliveCountMax 3
```


### on local machine run
```
ssh -N -f tensorboard-server
```

Now in browser go to [localhost:6006](localhost:6006)

### issues
if could not connect to server, clean vscode cached data:
```
rm -rf ~/.vscode-server
```