# 管理你的应用程序


## 文件系统布局

```shell
├── account-service
├── infrastructure
│   ├── development
│   │   ├── crd.yml
│   │   ├── dashboard-route.yml
│   │   ├── rbac.yml
│   │   └── traefik.yml
│   ├── release
│   └── testing
└── whoami
    ├── current
    └── v1
```

* kubectl apply -f ./


## Helm


Helm是一个 Kubernetes 的包管理工具，类似Linux中的yum/apt等。

### Install

[二进制文件](https://github.com/helm/helm/releases/latest)，加入系统Path.


## 主要概念

* helm：一个命令行客户端工具，主要用于Kubernetes应用chart的创建、打包、发布和管理
* Chart：应用描述，一系列用于描述 k8s 资源相关文件的集合
* Release：基于Chart的部署实体，一个 Chart 被 Helm 运行后将会生成对应的一个 release；将在k8s中创建出真实运行的资源对象
* Repository：主要就是用来存放和共享 Chart 使用，相当于是 GitHub，不过这里主要是供 Kubernetes 使用。

注意: v2版需要初始化一个Server组件

## 仓库

* 主仓库: helm repo add bitnami https://charts.bitnami.com/bitnami
* 国内: https://kubernetes.oss-cn-hangzhou.aliyuncs.com/charts
* 其它根据应用发布地址，如 https://fission.github.io/fission-charts/

* web hub: https://artifacthub.io/packages/search?kind=0

## Install Nginx

* helm search repo nginx
* helm install web-server bitnami/nginx -n whoami --create-namespace [--version 13.2.8]
* helm ls -n whoami
* helm upgrade web-server bitnami/nginx --set service.type="ClusterIP" -n whoami
* 查阅更多参数: https://artifacthub.io/packages/helm/bitnami/nginx
* helm history web-server -n whoami
* helm rollback web-server [REVISION] -n whoami

## 制作自己的Chart


* helm create knm-charts
* helm pacakge knm-charts
* copy tgz to knm-repo
* helm repo index knm-repo --url http://localhost/charts
* helm repo add knm-repo http://localhost/charts

## Kustomize