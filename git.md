### 查看git版本

`git --version`

### 全局配置

`git config --global user.name "$1" #用户名`
`git config --global user.email "$2" #邮箱
`

### 生成密钥ssh-keygen

`ssh-keygen -t rsa -C "$3" #邮箱`
`ssh-keygen -t rsa -C "邮箱@qq.com"`

### 查看位置

`ls ~/.ssh`

### 测试连接仓库ssh

`ssh -T git@github.com`
`ssh -T git@gitee.com`

确保NEW上的两个文件的权限是正确的，id_rsa是600，id_rsa.pub是644，比如：
-rw------- 1 fancy fancy 1675 2013-03-19 12:55 id_rsa
-rw-r--r-- 1 fancy fancy 406 2013-03-19 12:55 id_rsa.pub

### clone

`git clone https://18439406854:1999y4m30d@gitee.com/`

### 克隆私有项目

`git clone https://gitee.com/gpg-dev/docker-app.git`

### 使用以下命令clone

`git clone https://用户名:密码@github.com/用户名/仓库名.git`           
`git clone https://zhangsan:123456@github.com/Zhangsan/springboot-demo.git`             
`git clone https://18439406854:1999y4m30d@gitee.com/gpg-dev/docker-app.git`

### 共有仓库

`git clone https://18439406854:1999y4m30d@gitee.com/gpg-dev/ruoyi-vue-pro.git`

### URL using bad/illegal format or missing URL

** git使用用户名密码clone的方式：**
git clone http://username:password@remote
** 例如：我的用户名是abc@qq.com,密码是abc123456,git地址为git@xxx.com/www.git**
git clone http://abc@qq.com:abc123456@git.xxx.com/www.git
** 执行报错：**
fatal: unable to access 'http://abc@qq.com:abc123456@git.xxx.com/www.git/':URL using bad/illegal format or missing URL
报错原因是因为用户名包含了@符号，所以需求要把@转码一下
<?php
$userame='abc@qq.com';
echo urlencode($userame);
?>

abc%40qq.com
@符号转码后变成了%40，所以只需在clone时将username变为abc%40qq.com即可，再次执行就ok了。
为了防止密码中也可能会有@，我觉得在拼接之前，可以对用户名和密码分别进行编码操作。
