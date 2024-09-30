## coreDNS教程

官网下载并解压到 /usr/local/bin,<br/>

#### <b>注</b>:根据实际情况修改以下内容

### 注册为service

```
[Unit]
Description=CoreDNS

[Service]
Type=notify
ExecStart=coredns -conf /data/coredns/Corefile
```

### 编写Corefile
例如
```
.:53 {
    errors
    health
    ready
    kubernetes cluster.local in-addr.arpa ip6.arpa {
        pods insecure
        upstream /etc/resolv.conf
        fallthrough in-addr.arpa ip6.arpa
    }
    prometheus :9153
    forward . /etc/resolv.conf
    cache 30
    loop
    reload
    loadbalance
}
import "/data/coredns/zones/*"
```

### 编写分片文件

例如
#### hosts类型:
```
my-app.com {
    hosts {
       xx.xx.xx.xx my-app.com
     }
 }      
```
#### CName类型:
```
$ORIGIN example.org.
@	3600 IN	SOA sns.dns.icann.org. noc.dns.icann.org. (
				2017042745 ; serial
				7200       ; refresh (2 hours)
				3600       ; retry (1 hour)
				1209600    ; expire (2 weeks)
				3600       ; minimum (1 hour)
				)

	3600 IN NS a.iana-servers.net.
	3600 IN NS b.iana-servers.net.

www     IN A     127.0.0.1
        IN AAAA  ::1
```
