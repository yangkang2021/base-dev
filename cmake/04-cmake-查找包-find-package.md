# find_package

## 通过库添加
1. find_package的作用与实例
    - CMAKE_MODULE_PATH
2. find_package的查询路径与设置
3. EXPORT：从自有项目创建cmake package
4. FindXXX.cmake：从头文件库文件创建cmake package
5. PkgConfig的pkg_check_modules把pkg-config的pc转成cmake

## 通过源码添加
1. git子模块 + sub_dir
1. FetchContent_Declare(用前者)或者ExternalProject_Add从git仓库或者http添加库

## 通过工具
1. vcpkg

## 参考
1. https://blog.csdn.net/baidu_35692628/article/details/132724130

