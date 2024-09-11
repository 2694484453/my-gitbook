### 重新加载 Docker 服务

`sudo systemctl daemon-reload`

### 重启 Docker 服务

`sudo systemctl restart docker`

### 查看 Docker 服务状态

`sudo systemctl status docker`

### proxy

```
{
"registry-mirrors": [
    "https://docker.fxxk.dedyn.io",
    "https://docker.registry.cyou",
    "https://docker-cf.registry.cyou",
    "https://docker.jsdelivr.fyi",
    "https://dockercf.jsdelivr.fyi",
    "https://dockerpull.com",
    "https://dockerproxy.cn",
    "https://hub.uuuadc.top",
    "https://docker.1panel.live",
    "https://hub.rat.dev",
    "https://docker.anyhub.us.kg",
    "https://docker.ckyl.me",
    "http://hub-mirror.c.163.com",
    "https://docker.mirrors.ustc.edu.cn",
    "https://registry.docker-cn.com"
    ]
}
```

### 批量查找镜像仓库源

`docker images -f reference=111/222/333`

### 批量模糊查找镜像仓库源

`docker images -f reference=111/222/*`      
`docker images -f reference=*/222/*`

### 批量查找镜像id

`docker image ls -a -q 111/222/333`

### 批量模糊查找镜像id

`docker image ls -a -q -f reference=*/222/*`

### 批量删除镜像

`docker rmi $(docker image ls -a -q 111/222/333)`       
`docker rmi $(docker image ls -a -q -f reference=*/222/*)`      

### 其他
```
Usage: docker images [OPTIONS] [REPOSITORY[:TAG]]
Options:
  -a, --all 显示所有镜像
  -f, --filter filter 使用过滤器过滤镜像
    dangling true or false, true列出没有标签的，false相反
    label (label=<key> or label=<key>=<value>)，如果镜像设置有label，则可以通过label过 滤
    before (<image-name>[:<tag>], <image id> or <image@digest>) - 某个镜像前的镜像
    since (<image-name>[:<tag>], <image id> or <image@digest>) - 某个镜像后的镜像
    reference (pattern of an image reference) - 模糊查询,例：--filter reference='busy*:*libc' 
  --format string 格式化输出
    .ID 镜像ID
    .Repository 镜像仓库
    .Tag 镜像tag
    .Digest Image digest
    .CreatedSince 创建了多久
    .CreatedAt 镜像创建时间
    .Size 镜像大小
-q, --quiet 只显示镜像ID
```
