---
description: 基于nacos的实时动态文件配置来管理k8s集群config文件
---

# 0⃣ Nacos+k8s集群动态配置与管理



## 准备环境

* [x] minikube
* [x] kubectl
* [x] nacos
* [x] kubeconfig



## 步骤

#### 简单实验

* nacos中创建命名空间，如 kube并导入config文件

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>



* 找到nacos产生的配置文件路径，如/home/nacos/kube/DEFAULT\_GROUP/xxx，执行查看配置

```sh
kubectl config view --kubeconfig=/home/nacos/kube/DEFAULT_GROUP/configxxx
```

```
C:\Users\Administrator\Desktop>kubectl config view --kubeconfig=C:\Users\Administrator\.kube\config179
apiVersion: v1
clusters:
- cluster:
    certificate-authority: C:\Users\Administrator\.minikube\ca.crt
    extensions:
    - extension:
        last-update: Mon, 05 Jun 2023 10:43:56 CST
        provider: minikube.sigs.k8s.io
        version: v1.26.0
      name: cluster_info
    server: https://127.0.0.1:60646
  name: minikube
contexts:
- context:
    cluster: minikube
    extensions:
    - extension:
        last-update: Mon, 05 Jun 2023 10:43:56 CST
        provider: minikube.sigs.k8s.io
        version: v1.26.0
      name: context_info
    namespace: default
    user: minikube
  name: minikube
current-context: minikube
kind: Config
preferences: {}
users:
- name: minikube
  user:
    client-certificate: C:\Users\Administrator\.minikube\profiles\minikube\client.crt
    client-key: C:\Users\Administrator\.minikube\profiles\minikube\client.key
```
