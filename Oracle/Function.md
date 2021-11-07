<!--
 * @Author: Outsider
 * @Date: 2021-11-03 21:16:57
 * @LastEditors: Outsider
 * @LastEditTime: 2021-11-07 17:05:18
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\Function.md
-->
# Oracle简单函数
## 单行函数
### 字符函数
- str1||str2
  - 拼接字符串str1和str2

- ASCII(x)  
  - return 字符x的ASCII码值

- LENGTH(x)
  - return x的字符个数
- CONCAT(x,y)
  - 将y加到x上，并返回结果

- LOWER(x)
  - 把x中的字母转换成小写，并返回结果

- SUBSTR(x,start[,length])
  - 返回x中的一个字符串
  - 字符串长度从start开始
  - 可以指定长度

### 数字函数
- ABS(n):返回n的绝对值
- ACOS(n):反余弦
- SIN(n):正弦
- MOD(m,n)：m除n的模
- EXP(n):e的n次幂
- POWER(m,n):m的n次幂
- LOG(m,n):m为底n的对数
- LN(n):e为底的n的对数
- CEIL(n):小于等于n的最小整数
- FLOOR(n):大于等于n的最大整数
- ROUND(n,[m]):四舍五入到m位，省略m四舍五入到整数
- SIGN(n):检查数字的正负

### 日期时间函数
- CURRENT_DATE:当前日期
- CURRENT_TIME:当前时间
- CURRENT_TIMESTAMP:当前日期时间
- EXTRACT(date FROM datetime):从日期中获取特定数据
  - date:YEAR,MONTH,DAY,HOUR
- LAST_DAY(d):返回日期所在月份的最后一天
- MONTHS_BETWEEN(d1,d2):返回相差的月数
  
## 转换函数
- CAST(current_value AS data_type)
  - 类型转换

