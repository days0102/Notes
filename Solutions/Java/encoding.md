<!--
 * @Author: Outsider
 * @Date: 2021-10-30 19:52:41
 * @LastEditors: Outsider
 * @LastEditTime: 2021-10-30 19:57:08
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Solutions\Java\encoding.md
-->
## Windows终端编译java文件乱码（编码 GBK 的不可映射字符）
> 原因：Windows终端使用中文的编码方式和Java文件的编码方式不同
- chcp //查看Windows终端编码方式
  - 936为GBK编码
  - 65001为UTF-8编码

> 解决：在使用javac时指定编码方式
> - javac -encoding [编码方式] [文件名]