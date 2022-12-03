# Docker

## Windows/MacOS

Windows及MacOS系统推荐安装[Docker Desktop](https://www.docker.com/products/docker-desktop/)，最新预览版可进行WASM(WebAssembly)。

## Linux

(略)

## docker cli

* docker version: 查阅版本
* docker info: 显示docker系统信息，重点关注Cgroup Driver: cgroupfs/systemd，Kubernetes要与之一致
* docker pull: 拉取镜像
* docker run: 运行镜像
* docker exec: 执行容器中的命令

## 国内镜像配置

```json
{
"registry-mirrors": [
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