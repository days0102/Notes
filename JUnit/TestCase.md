## TestCase类（JUnit框架的核心类）
- TestCase类位于junit.framework包中
- TestCase类继承自Assert类，可直接使用Assert类中相关的方法
- TestCase类可以包含多个测试用例
## 主要方法
|方法|描述|
|:--:|:--:|
|void setUp()|创建固定测试，如打开一个网络链接|
|void tearDown()|拆除固定设置|
|String toString()|返回测试用例的一个字符串表示|
