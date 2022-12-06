# Kubernetes


## Version

### Kubernetes in docker desktop

* 修改为国内镜像, Docker Engine registry-mirrors

```json
  "registry-mirrors": [
    "https://registry.cn-hangzhou.aliyuncs.com"
  ]
```

### Minikube

[官网下载](https://minikube.sigs.k8s.io/docs/start/) 或 Docker desktop中开启

### K3s

[K3s官网](https://k3s.io)

### Kubernetes Cluster

* (安装略)
* ETCD + coreDNS + kube-apiserve + kube-controller-manager + kube-scheduler + kube-proxy + fannled + kubelet

## kubectl

* 使用Kubernetes API和Kubernetes通信的命今行工具


## 基本概念

### POD

* Pod 是 k8s 中集群部署应用和服务的最小单元，一个 pod 中可以部署多个容器
* kubectl get pods -n kube-system

### ReplicaSet

*　副本集

### Deployment

* Deployment 提供了一种对 Pod 和 ReplicaSet 的管理方式，每一个 Deployment 都对应集群中的一次部署
* kubectl get deployment

### Service

* 通过对外暴露服务方式访问POD，基于Label标签选择POD或DNS
* 方式: ClusterIP/NodePort/LoadBalancer


### Ingress Controller

* 反向代理
* Nginx Ingress/Traefik Ingress
