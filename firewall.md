# linux防火墙配置

## 在CentOS中，可以使用firewalld作为防火墙。以下是查看和添加防火墙规则的方法：

### 查看防火墙状态：

`sudo systemctl status firewalld`

### 启动防火墙：

`sudo systemctl start firewalld`

### 停止防火墙：

`sudo systemctl stop firewalld`

### 设置开机自启：

`sudo systemctl enable firewalld`

### 取消开机自启：

`sudo systemctl disable firewalld`

### 查看已添加的防火墙规则：

`sudo firewall-cmd --list-all`

### 添加防火墙规则（允许SSH端口22）：

`sudo firewall-cmd --zone=public --add-port=22/tcp --permanent`

### 重新加载防火墙配置：

`sudo firewall-cmd --reload`
