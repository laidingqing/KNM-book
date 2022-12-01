# 创建项目骨架

通过以下三种方式创建Quarkus项目骨架，注意：Quarkus基于JDK 11或17，Maven 3.8.1+

## 在线项目生成器

[官网在线生成](https://code.quarkus.io)

* 打开网站
* 修改项目配置信息：Group、Artifact、Version、Java Version、Build Tool
* 选择所需依赖项，最精简项选择: RESTEasy Classic 或 RESTEasy Classic JSON-B/RESTEasy Classic Jackson
* 生成并下载代码文件
* 使用IDE打开项目

## 使用Maven插件

```shell
mvn io.quarkus:quarkus-maven-plugin:2.1.3.Final:create \
-DprojectGroupId=quarkus \
-DprojectArtifactId=account-service \
-DclassName="quarkus.accounts.AccountResource" \
-Dpath="/accounts"

```

## 手动

对Maven项目管理及Quarkus组件较熟悉可以使用该方法

## 运行

* mvn quarkus:dev
* mvn package & java -jar target/quarkus-app/quarkus-run.jar
* 访问 http://localhost:8080