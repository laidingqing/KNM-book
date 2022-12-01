# 打包与部署



## JVM


### Docker

* mvn clean package -Dquarkus.container-image.build=true
* 自动生成容器镜像, docker images 查看



## Native

使用AOT编译方式打包为一个二进制可执行文件

### Requirement

* [Graalvm](https://www.graalvm.org/downloads)，选择对应版本，需对应操作系统平台、Java版本及CPU架构，[Release Notes](https://www.graalvm.org/release-notes/20_3/)查阅对应Java版本
* JAVA_HOME及PATH需要相应更改，推荐使用sdkman管理
* Native-image: gu install native-image

### 配置

* Maven中增加名称为native的profile，并配置构建设置，示例如下代码块
* mvn clean package -Pnative
* 运行target目录下可执行文件

```xml

<profile>
	<id>native</id>
	<activation>
		<property>
			<name>native</name>
		</property>
	</activation>
	<build>
		<plugins>
			<plugin>
				<artifactId>maven-failsafe-plugin</artifactId>
				<version>3.0.0-M7</version>
				<executions>
					<execution>
						<goals>
							<goal>integration-test</goal>
							<goal>verify</goal>
						</goals>
						<configuration>
							<systemPropertyVariables>
								<native.image.path>${project.build.directory}/${project.build.finalName}-runner</native.image.path>
							</systemPropertyVariables>
						</configuration>
					</execution>
				</executions>
			</plugin>
		</plugins>
	</build>
	<properties>
		<quarkus.package.type>native</quarkus.package.type>
	</properties>
</profile>

```

### 构建Docker镜像

* mvn clean package -Pnative -Dquarkus.native.container-build=true
* docker buildx build -f src/main/docker/Dockerfile.native -t quarkus/account-service-native .
* docker images
* docker run -i --rm -p 8080:8080 [6277ea9f713e]