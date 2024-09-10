## etcd操作
#### 启动etcd：


```
etcd --name m1 --initial-advertise-peer-urls http://127.0.0.1:2380 --listen-peer-urls http://127.0.0.1:2380 --listen-client-urls http://127.0.0.1:2379 --advertise-client-urls http://127.0.0.1:2379 --initial-cluster-token etcd-cluster-1 --initial-cluster m1=http://127.0.0.1:2380 --initial-cluster-state new
```


#### 查询所有key
```
etcdctl get --prefix ""
```


#### 查询指定地址所有key
```
etcdctl get --prefix "" --endpoints=192.168.146.25:12379
```

#### 指定名称启动
```
etcd --name m1 --initial-advertise-peer-urls http://127.0.0.1:2380 --listen-peer-urls http://127.0.0.1:2380 --listen-client-urls http://127.0.0.1:2379 --advertise-client-urls http://127.0.0.1:2379 --initial-cluster-token etcd-cluster-1 --initial-cluster m1=http://127.0.0.1:2380 --initial-cluster-state new
```

#### 备份
```
etcdctl --endpoints 127.0.0.1:2379 snapshot save D://data//gpg0202.db
```

#### 恢复
```
etcdctl snapshot restore D://data//etcd//gpg0202.db --name m1 --initial-cluster m1=http://127.0.0.1:2380 --initial-cluster-token etcd-cluster-1 --initial-advertise-peer-urls http://127.0.0.1:2380
```

#### 指定重启

```
etcd --name m1 --listen-client-urls http://127.0.0.1:2379 --advertise-client-urls http://127.0.0.1:2379 --listen-peer-urls http://127.0.0.1:2380 
```
