## 密码

`sudo passwd root`

### 防火墙

`ufw enable | disable`

### 设置host

`sudo gedit /etc/hosts`   
保存并重启网络  
`sudo /etc/init.d/networking restart`

### 查看时区

`date -R`

### 选择时区

`tzselect`  
4-亚洲

### 静态ip

`https://cloud.tencent.com/developer/article/1933335`

### 镜像源：

`vi /etc/apt/sources.list.d`

### 镜像源地址

```
deb https://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
deb-src https://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse

deb https://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
deb-src https://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse

deb https://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src https://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse

#deb https://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse

#deb-src https://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse

deb https://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src https://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
```

### 更新镜像源

`sudo apt-get update`   
`sudo apt-get upgrade`

### 内存

`free -m`

### 存储空间

`df -hl：查看磁盘剩余空间`  
`df -h：查看每个根路径的分区大小`   
`du -sh [目录名]：返回该目录的大小`   
`du -sm [文件夹]：返回该文件夹总M数`    
`du -h [目录名]：查看指定文件夹下的所有文件大小（包含子文件夹）`

### 显示文件/文件夹

`du -sh extensions`

### 环境变量

`vim /etc/profile`   
在profile中添加：`export PATH="/root/ubuntu/binaries/:$PATH"`
执行`source /etc/profile`命令更新配置

### 软连接

`ln -s /home/ide/167350/nodejs/bin/node /usr/bin/node  `        
`ln -s /home/ide/167350/nodejs/bin/npm /usr/bin/npm`

### 统一

`ln -s /usr/local/nodejs/bin/node /usr/bin/node`    
`ln -s /usr/local/nodejs/bin/npm /usr/bin/npm`      
`ln -s /usr/local/nodejs/bin/npm /usr/local/bin/npm`

### jdk

`ln -s /usr/local/jdk8/bin/java /usr/bin/java`

### mvn

`ln -s /usr/local/maven/bin/mvn /usr/bin/mvn`
`ln -s /usr/local/maven/bin/mvnDebug /usr/bin/mvnDebug`

### 暂时清除所有环境变量

`export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin`

export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_321.jdk/Contents/Home/
export PATH=$PATH:$JAVA_HOME/bin

export JAVA_HOME=/usr/local/jdk8
export PATH=$PATH:$JAVA_HOME/bin

export MAVEN_HOME=/Users/gaopuguang/apache-maven-3.9.0
export PATH=$PATH:$MAVEN_HOME/bin

export MAVEN_HOME=/usr/local/apache-maven-3.5.0
export PATH=
$PATH:
$MAVEN_HOME/bin
export JAVA_HOME=/Library/Java/JavaVirtualMachines/temurin-8.jdk/Contents/Home
export PATH=
$PATH:
$JAVA_HOME/bin

登录权限：

### 配置root登录

`vim /etc/ssh/sshd_config`      
`PermitRootLogin yes`       
`PermitEmptyPasswords yes`      
重启 `ssh service sshd restart`

### 开机启动：

1.编辑rc.local文件          
`[root@localhost ~]# vi /etc/rc.local`
2.修改rc.local文件，在 exit 0 前面加入以下命令。保存并退出。       
`/etc/init.d/mysqld start # mysql开机启动`      
`/etc/init.d/nginx start # nginx开机启动`       
`supervisord -c /etc/supervisor/supervisord.conf # supervisord开机启动`         
`/bin/bash /server/scripts/test.sh >/dev/null 2>/dev/null`      
3.最后修改rc.local文件的执行权限       
`[root@localhost ~]# chmod +x /etc/rc.local`            
`[root@localhost ~]# chmod 755 /etc/rc.local`

### 注册开机启动服务
### suidao网络穿透服务开机启动项
[Unit]         
Description=suidao      
[Service]       
Type=simple     
WorkingDirectory=/soft/suidao/      
ExecStart=/soft/suidao/./SuiDao.Client      
[Install]       
WantedBy=multi-user.target


### 查找文件：
`find / -name kubectl`  或者
`whereis xxx`
### 压缩、解压：
### 压缩     
`tar -zcvf xxx.tar.gz sourcedir`        
### 解压     
`tar -zxvf xxx.tar.gz`
文件挂载：       
### 查看硬盘挂载情况       
`fdisk -l`          
### 查看当前分区情况       
`df -l`     
### 给新硬盘添加新分区           
`fdisk /dev/vdb`        
### 分区完成，查询所有设备的文件系统类型            
`blkid` 

### 挂载
#挂载需要将硬盘挂载在挂载点上（一个文件夹），但是mount并不会创建文件夹，所以在使用mount命令之前首先创建挂载点
#--查看/dev/sfdb1的格式
`blkid`
 

mkdir /mnt/storage
将新分区 /dev/vdb1 挂载到/mnt/storage挂载点下

mount /dev/vdb1 /mnt/storage/
mount /dev/vdb /ebs
mount -t ext4 /dev/vdb /ebs

#格式化
mkfs.xfs -f /dev/vdb
mkfs.ext4 -f /dev/sdb
#查看是否挂载成功
mount

1、df -h #查看硬盘挂载的节点
2、sudo umount /dev/*** # （***挂载的节点）解除挂载
3、sudo -i（sudo su）#切换到 root 用户下
4、mkfs.ext4 /dev/*** #将硬盘格式化成 ext4 格式
5、mount /dev/*** /media/*** # （mount /dev/sda /media/ubuntu）硬盘挂载
6、格式化完成。（下一步，更改盘符名称）
7、df -h #查看硬盘挂载的节点 （附录也可以实现）
8、sudo umount /dev/*** # （***挂载的节点）解除挂载
9、sudo e2label /dev/*** newname #更改盘符名称 eg：sudo e2label /dev/sda1 MKZ015
10、mount /dev/*** /media/*** # （mount /dev/sda /media/ubuntu）硬盘挂载
开机自动挂载
#查看uuid
blkid
UUID="db32cc57-4511-4efb-8f31-938ff92ad2fd"
#挂载到 /etc/fstab
echo "UUID=e943fbb7-020a-4c64-a48a-2597eb2496df /vdb1 ext4 defaults 0 0" >> /etc/fstab
echo "UUID=f3471f7b-a676-4f54-92d1-4f26e4ddf88d /sdb ext4 defaults 0 0" >> /etc/fstab

/dev/nvme0n1p1: UUID="F73D-BB1F" TYPE="vfat" PARTUUID="bc35dc78-3d7f-458f-bd8c-1059fcb5a4ae"
/dev/nvme0n1p2: UUID="2f49137e-6988-43b2-aafa-77b0bb67cef6" TYPE="ext4" PARTUUiID="73987121-275a-472f-a678-d9c728c273f2"
/dev/nvme0n1p3: UUID="pWejAN-yBnf-JLrk-gXYk-5rNR-WSrO-We137z" TYPE="LVM2_member" PARTUUID="
d7a12983-58b8-4670-835a-4afd0d35da25"
/dev/sdb1: LABEL="1804M-iM-+M-^XM-fM-^YM-.M-eM-^EM-^I" UUID="D6DE13E6DE13BDA5" TYPE="ntfs" PARTUUID="b2c644dd-01"
/dev/sda: UUID="f3471f7b-a676-4f54-92d1-4f26e4ddf88d" TYPE="ext4"
/dev/mapper/ubuntu--vg-ubuntu--lv: UUID="c9a3dacb-bd91-4c73-87bf-dbe4b4105f33" TYPE="ext4"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
root@ubuntu:/sda/share# vi /etc/fstab
/dev/disk/sdc1/by-uuid/f3471f7b-a676-4f54-92d1-4f26e4ddf88d /sdc ext4 defaults 0 1
/dev/disk/sdb1/by-uuid/D6DE13E6DE13BDA5 /sdb ntfs defaults 0 1
/dev/disk/sda1/by-uuid/AC3C7E1D3577D220 /sda ext4 defaults 0 1

#或者
vim /etc/fstab
#将 /etc/fstab 中定义的所有档案系统挂上。
mount -a
df -h
#查看已经挂载上，说明配置没有问题，再重启机器。

2、检查
longqiping@ubuntu:~$ df /tmp
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv 65019484 62892356 0 100% /
发现/tmp所在的/即ubuntu--vg-ubuntu--lv的空间没有了。
查看lvm卷组的信息
root@ubuntu:/home/longqiping# vgdisplay
--- Volume group ---
VG Name ubuntu-vg
System ID             
Format lvm2
Metadata Areas 1
Metadata Sequence No 2
VG Access read/write
VG Status resizable
MAX LV 0
Cur LV 1
Open LV 1
Max PV 0
Cur PV 1
Act PV 1
VG Size               <126.50 GiB
PE Size 4.00 MiB
Total PE 32383
Alloc PE / Size 16192 / 63.25 GiB
Free PE / Size 16191 / <63.25 GiB
VG UUID 8cak6E-4fZv-kGgq-lsOA-9FHC-Ju7R-kn2RJy
3、解决
使用命令进行磁盘扩容
lvextend -L 10G /dev/mapper/ubuntu--vg-ubuntu--lv //增大或减小至19G
lvextend -L +10G /dev/mapper/ubuntu--vg-ubuntu--lv //增加10G
lvextend -L +800G /dev/mapper/ubuntu--vg-ubuntu--lv //增加10G
lvreduce -L -10G /dev/mapper/ubuntu--vg-ubuntu--lv //减小10G
lvresize -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv //按百分比扩
lvresize -l +90%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
使用如下命令，将/tmp增加60G
root@ubuntu:/home/longqiping# lvresize -L +60G /dev/mapper/ubuntu--vg-ubuntu--lv
Size of logical volume ubuntu-vg/ubuntu-lv changed from 63.25 GiB (16192 extents) to 123.25 GiB (31552 extents).
Logical volume ubuntu-vg/ubuntu-lv successfully resized.
扩容
root@ubuntu:/home/longqiping# resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
resize2fs 1.45.5 (07-Jan-2020)
Filesystem at /dev/mapper/ubuntu--vg-ubuntu--lv is mounted on /; on-line resizing required
old_desc_blocks = 8, new_desc_blocks = 16
The filesystem on /dev/mapper/ubuntu--vg-ubuntu--lv is now 32309248 (4k) blocks long.
看看效果
root@ubuntu:/home/longqiping# vgdisplay
--- Volume group ---
VG Name ubuntu-vg
System ID             
Format lvm2
Metadata Areas 1
Metadata Sequence No 3
VG Access read/write
VG Status resizable
MAX LV 0
Cur LV 1
Open LV 1
Max PV 0
Cur PV 1
Act PV 1
VG Size               <126.50 GiB
PE Size 4.00 MiB
Total PE 32383
Alloc PE / Size 31552 / 123.25 GiB
Free PE / Size 831 / <3.25 GiB
VG UUID 8cak6E-4fZv-kGgq-lsOA-9FHC-Ju7R-kn2RJy

root@ubuntu:/home/longqiping# df -h
Filesystem Size Used Avail Use% Mounted on
udev 16G 0 16G 0% /dev
tmpfs 3.2G 1.5M 3.2G 1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv 122G 61G 56G 52% /
tmpfs 16G 0 16G 0% /dev/shm
tmpfs 5.0M 0 5.0M 0% /run/lock
tmpfs 16G 0 16G 0% /sys/fs/cgroup
/dev/vda2 976M 396M 514M 44% /boot
/dev/loop0 49M 49M 0 100% /snap/core18/1883
/dev/vda1 511M 3.5M 508M 1% /boot/efi
/dev/loop1 49M 49M 0 100% /snap/core18/1990
/dev/loop2 27M 27M 0 100% /snap/snapd/11043
/dev/loop3 29M 29M 0 100% /snap/snapd/11115
/dev/loop5 62M 62M 0 100% /snap/lxd/19206
/dev/loop4 63M 63M 0 100% /snap/lxd/19648
tmpfs 3.2G 0 3.2G 0% /run/user/1000
