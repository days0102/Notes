# CMake语法
## CMake预定义的变量
- PROJECT_SOURCE_DIR : 工程根目录
- PROJECT_BINARY_DIR : 运行cmake命令的目录
- CMAKE_CURRENT_SOURCE_DIR : 当前处理的CMakeLists.txt文件所在路径

## 常用语法
- cmake_minimum_required(VERSION ××)
  - 可选，不一定要写。用于说明CMake最低版本
  - 一般放置在CMakeLists.txt文件的开头
  - ex : cmake_minimum_required(VERSION 2.6)#指定最低版本至少为2.6
- project(项目名称)
  - 指定项目的名称
  - ex : project(Hello)#指定项目的名称为Hello
  - 执行了该条指令之后，将会自动创建两个变量
    - < projectname >_BINARY_DIR : 二进制文件保存路径；
    - < projectname >_SOURCE_DIR : 源代码路径；