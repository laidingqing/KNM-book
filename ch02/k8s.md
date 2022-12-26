# Kubernetes


也称为 K8s，是用于自动部署、扩缩和管理容器化应用程序的开源系统。

* 自动化上线和回滚
* 服务发现与负载均衡
* 自我修复
* 水平扩缩

## Version

### Kubernetes in docker desktop

* 修改为国内镜像, Docker Engine registry-mirrors

```json
  "registry-mirrors": [
    "https://registry.cn-hangzhou.aliyuncs.com"
  ]
```

### Minikube

[官网下载](https://minikube.sigs.k8s.io/docs/start/) 

* 安装二进制文件
* minikube start --image-mirror-country=cn --image-repository=registry.cn-hangzhou.aliyuncs.com/google_containers --driver=docker


### MicroK8s


[官网](https://microk8s.io/)
 

### K3s

[K3s官网](https://k3s.io)

### Kubernetes Cluster

* kubeadm (安装略)
* ETCD + coreDNS + kube-apiserve + kube-controller-manager + kube-scheduler + kube-proxy + fanneld + kubelet



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
* kubectl get svc/service

### Ingress Controller

* 从集群外访问集群内服务的路由控制器
* Nginx Ingress/Traefik Ingress/Envoy Ingress/HAProxy Ingress/Apache APISIX/Istio Ingress
* kubectl get ingress


## kubectl

* 使用Kubernetes API和Kubernetes通信的命今行工具


### 基本命令

* kubectl get (componentstatuses/nodes/pods/deployment/service/ingress) [-n namespace]
* kubectl logs (pod name) [-n namespace]
* kubectl describe (name) [-n namespace]



## Kubernetes 如何运行Docker

* 调用CRI: Container Runtime Interface(Kubernates API)
* 调用Containerd/CRI-O(容器运行时)
* 根据OCI规范调用runc（容器镜像生成同时遵守OCI规范）
* 完成容器处理



## 部署


### YAML



### Helm
