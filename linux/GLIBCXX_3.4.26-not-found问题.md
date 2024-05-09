# [GLIBCXX_3.4.26-not-found问题.md](GLIBCXX_3.4.26-not-found%CE%CA%CC%E2.md)

1. 现象
    - 阿里云ecs的centos版本太低，gcc4.8.5
2. 原因：
    - 编译环境版本高于运行版本
3. 解决办法： 去运行环境的ecs上编译
4. 解决：遇到gcc版本太低有些特性不支持：
   ```
   https://www.jianshu.com/p/e3ec54e30346
   
   yum install centos-release-scl
   yum install devtoolset-8-gcc*
   
   临时生效：
   source /opt/rh/devtoolset-8/enable
   ```
