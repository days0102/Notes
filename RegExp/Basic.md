<!--
 * @Author: Outsider
 * @Date: 2022-01-26 13:05:56
 * @LastEditors: Outsider
 * @LastEditTime: 2022-01-26 14:19:06
 * @Description: In User Settings Edit
 * @FilePath: \Notes\RegExp\Basic.md
-->

# 正则表达式

## 语法
- ^ : 匹配字符串开始位置
- $ : 匹配字符串结束位置
- [abc] : 匹配[]中的所有字符(abc)
- [^abc]: 匹配除[]中的所有字符
- [a-f] : 匹配-区间的所有字符
- .     : 匹配除换行符(\r、\n)之外的任意单个字符相当于[^\r\n]
- ()    : 标记一个子表达式的开始和结束位置。子表达式可以获取供以后使用


## 限定符
- ?     : 匹配前面的子表达式零次或一次，或指明一个非贪婪限定符
- *     : 匹配前面的子表达式零次或多次
- +     : 匹配前面的子表达式一次或多次