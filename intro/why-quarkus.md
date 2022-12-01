# 为什么是Quarkus?

## Java开发部署中的一些问题

* 不够轻量
* 也不够快速

## Live-Coding

* 代码实时运行时改动
* 无需重启JVM

## 规范支持

MicroProfile 4.0

## 运行效率

### 启动到第一个HTTP响应用时

<table>
	<thead>
		<tr>
			<th>Application</th>
			<th>Traditional</th>
			<th>Quarkus JVM</th>
			<th>Quarkus Native</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>REST Application</td>
			<td>4.3(s) </td>
			<td>0.934(s) </td>
			<td>0.016(s) </td>
		</tr>
		<tr>
			<td>CRUD Application</td>
			<td>9.5(s)  </td>
			<td>2.03(s)  </td>
			<td>0.042(s) </td>
		</tr>	
	</tbody>
</table>

### 内存使用

<table>
	<thead>
		<tr>
			<th>Application</th>
			<th>Traditional</th>
			<th>Quarkus JVM</th>
			<th>Quarkus Native</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>REST Application</td>
			<td>136(mb) </td>
			<td>73(mb)  </td>
			<td>12(mb)</td>
		</tr>
		<tr>
			<td>CRUD Application</td>
			<td>209(mb) </td>
			<td>145(mb)  </td>
			<td>28(mb)</td>
		</tr>	
	</tbody>
</table>



## Native AOT Compiler(二进制可执行文件)

* JIT: Just-In-Time
* AOT: Ahead-Of-Time，缺点是构建Native包花费更多时间

## 对比其它

* Spring Native
* Micronaut
