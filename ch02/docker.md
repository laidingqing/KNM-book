# Docker

## Windows/MacOS

Windows及MacOS系统推荐安装[Docker Desktop](https://www.docker.com/products/docker-desktop/)，最新预览版可进行WASM(WebAssembly)。

## Linux

(略)

## Docker如何工作

* docker cli 命令
* 调用Containerd(容器运行时)
* 根据OCI规范调用runc（容器镜像生成同时遵守OCI规范）
* 完成容器处理


## 基础镜像层

* Alpine Linux 发行版
* Debian slim发行版
* 查看: docker run -it [xxx] cat /etc/os-release

<b>仅提供标准C库，shell，包管理</b>
其它：Ubuntu、CentOS

## docker cli

* docker version: 查阅版本
* docker info: 显示docker系统信息，重点关注Cgroup Driver: cgroupfs/systemd，Kubernetes要与之一致
* docker pull: 拉取镜像
* docker run: 运行镜像
* docker exec: 执行容器中的命令

### docker run

* docker run --help
* docker run -p 80:80 -v /tmp/html:/usr/share/nginx/html nginx:latest

## docker-compose

* [docker-compose](https://github.com/docker/compose)
* docker-compose up/down

```yml
version: '3.1'

services:
  nginx:
    image: nginx:latest
    ports:
      - 80:80  
    volumes:
      - /var/nginx/html:/usr/share/nginx/html
      - /var/nginx/nginx.conf:/etc/nginx/nginx.conf
    privileged: true 
  mysql:
    image: mysql:5.7.27
    ports:
      - 3306:3306
    environment:
      - MYSQL_ROOT_PASSWORD=
  account-service:
    image: account-service:latest
    ports:
      - 8001:8001
    depends_on:
      - mysql
      - redis	  
```


## 国内镜像配置

```json
{
"registry-mirrors": [
    "https://registry.docker-cn.com",
    "https://docker.mirrors.ustc.edu.cn",
    "https://registry.cn-hangzhou.aliyuncs.com"
  ]
}  
```

* in Docker Engine
* in /etc/docker/daemon.json

## docker buildx/build

### Dockerfile

```txt
FROM registry.access.redhat.com/ubi8/openjdk-11:1.14

COPY --chown=185 target/quarkus-app/lib/ /deployments/lib/
COPY --chown=185 target/quarkus-app/*.jar /deployments/
COPY --chown=185 target/quarkus-app/app/ /deployments/app/
COPY --chown=185 target/quarkus-app/quarkus/ /deployments/quarkus/

EXPOSE 8080
ENTRYPOINT exec java -jar /deployments/quarkus-run.jar

```

### buildx/build

```shell
docker buildx build -f src/main/docker/Dockerfile.jvm -t quarkus-mp/account-service:v0.1.0 .
```
