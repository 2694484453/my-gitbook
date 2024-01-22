---
description: 基于nacos注册中心实现Prometheus的动态发现...
---

# 1⃣ Prometheus+Nacos动态监控发现

## 准备环境

* [x] 已部署Prometheus
* [x] 已部署Nacos

## 整合步骤

* 创建nacos命名空间，如Prometheus

<figure><img src=".gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

* 创建一个服务发现配置json文件，例如

```
[
  {
    "targets": [ "server.gpg123.vip:8090" ],
    "labels": {
      "job": "spring-boot-demo",
      "instance": "spring-boot-demo"
    }
  }
]
```



* 找到nacos文件产生的文件位置，将其路径添加到Prometheus的配置文件，例如（按照实际环境修改）

```
/home/nacos/data/tenant-config-data/
```

```
 - job_name: 'nacos_files'
    # 指定路径
    metrics_path: '/actuator/prometheus'
    # 收集数据的时间间隔
    scrape_interval: 5s
    file_sd_configs:
      - refresh_interval: 5s
        files:
          - ./nacos/prometheus/DEFAULT_GROUP/*.json
          - ./*.json

```



* 重启Prometheus，再nacos的Prometheus命名空间下添加.json文件，查看Prometheus面板Status->Targets，观察是否生效

<figure><img src=".gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
