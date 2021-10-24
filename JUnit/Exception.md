# 异常处理
## 失败和错误
- 失败(Failure):测试用例的结果与预期不相同
- 错误(Error):测试用例或方法错误
## 异常处理
- @Test(expected)
  - expected允许设置Throwable的子类
  - 用于检测待测方法是否正确抛出异常
  - 不能表明异常发生的位置
- ExpectedException
  - 需要用@Rule注解声明ExpectedException异常
  - 可以精确定位异常发生位置
```java
@Rule
public ExpectedException throw=ExpectedException.none();
```
- try/catch/finally