## 事务失效问题

使用事务时，如果使用try catch，异常会被catch捕获，而不会向外层抛出，所以外出的aop捕获不到异常，此时事务失效。

解决方案：手动回滚，catch内添加

```java
TransactionAspectSupport.currentTransactionStatus().setRollbackOnly();
```

