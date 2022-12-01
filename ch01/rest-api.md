# REST API

在已创建有Quarkus应用骨架下增加REST资源访问，完成获取账户服下账户列表、账户对象，以JSON格式输出，观察启动控制台日志，它是Live Coding。

## 增加REST资源

### 准备Account对象

```java
public class Account {
	public Long accountNumber;
	public String customerName;
	public Account(Long accountNumber, String customerName) {
	    this.accountNumber = accountNumber;
	    this.customerName = customerName;
	}
    public Long getAccountNumber() {
      return accountNumber;
    }
    public void setAccountNumber(Long accountNumber) {
      this.accountNumber = accountNumber;
    }
    public String getCustomerName() {
      return customerName;
    }
    public void setCustomerName(String customerName) {
      this.customerName = customerName;
    }
}
```


```java
@Path("/accounts")
public class AccountResource {
	Set<Account> accounts = new HashSet<>();
    @PostConstruct // A
    public void setup(){
      accounts.add(new Account(1L, "Mary"));
    }	
}
```

* Class 类
* 以@Path标注REST资源路径
* 通常以Resource结尾(类似Spring应用以Controller结尾)

### GetAccounts查询账户列表

```java
@GET // A
@Produces(MediaType.APPLICATION_JSON) // B
public Set<Account> getAccounts() { // C
	return return accounts;
}

```


* A - 指定请求方法
* B - 表明响应体为JSON格式
* C - 返回一个账户对象集合
* 未指定Path，则为主类Path请求路径

### GetAccount查询账户对象

```java
  @GET
  @Path("/{accountNumber}")
  @Produces(MediaType.APPLICATION_JSON)
  public Account getAccount(@PathParam("accountNumber") Long accountNumber){
    Optional<Account> account = accounts.stream().filter(acct -> acct.getAccountNumber().equals(accountNumber)).findFirst();
    return  account.orElseThrow( () -> new WebApplicationException(String.format("Account with of %d does not exist.", accountNumber) )); //
  }

```




## JAX-RS 说明

所在包路径：javax.ws.rs.*

* @Path
* @GET
* @PathParam
* @Produces

## 验证