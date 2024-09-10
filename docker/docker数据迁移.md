## docker数据迁移

### 停止服务

```
sudo systemctl stop docker
```

### 修改配置

```
cd /lib/systemd/system 
vi docker.service
cat /lib/systemd/system/docker.service
```
修改[service]，ExecStart部分

```
[Service]
Type=notify
# the default is not to use systemd for cgroups because the delegate issues still
# exists and systemd currently does not support the cgroup feature set required
# for containers run by docker
#ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock --graph=/home/docker
ExecReload=/bin/kill -s HUP $MAINPID
TimeoutSec=0
RestartSec=2
Restart=always

```

### 重启

```
systemctl daemon-reload
sudo service docker start
```
### 再次查看

```
docker info
```

```
Docker Root Dir: /home/docker
```

