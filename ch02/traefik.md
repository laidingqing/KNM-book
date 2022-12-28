# K8s Ingress


## Service NodePort的问题

* 必须带端口访问
* 应用越多，宿主机暴露端口越多，不安全
* 无法使用域名访问，或URI规则



## Ingress


* Ingress 公开从集群外部到集群内服务的 HTTP 和 HTTPS 路由。 流量路由由 Ingress 资源上定义的规则控制
* 由Ingress　Controller实现, [控制器项目](https://kubernetes.io/zh-cn/docs/concepts/services-networking/ingress-controllers/)

## Traefik 

![traefik](/assets/images/traefik-concepts-2.webp)

### Install 

* CRD
* RBAC
* DaemonSet

### IngressRoute 配置
