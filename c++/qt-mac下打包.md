# qt在mac下打包
> 方法：xcode打包，然后用命令拷贝不全的库和文件
> 
> 拷贝后签名xcode记得加上：Other Code Signing Flags --deep

## framework和xcframework的区别
- xcframework可以用于合并多个不同平台的framework

## mac: cmake, framework, dmg, qt
  - https://stackoverflow.com/questions/2908640/how-to-add-a-framework-to-cmake
  - https://stackoverflow.com/questions/17070101/why-i-cannot-link-the-mac-framework-file-with-cmake/18330634#18330634

## rpath
   - https://www.jianshu.com/p/bfa05ef3c482

## dmg
1. 步骤
    - 打开磁盘工具，文件—-新建映像—-空白镜像
    - 把XXX.app、应用的快捷方式，背景，图标拖到镜像里面，摆放好位置
    - 设置背景：右击，选择“查看显示选项”；最下面背景选择“图片“
    - 设置图标：commend+i 预览简介，将磁盘内的icon.icns文件拖到左上角替换
    - 隐藏背景或者图标？可以不用
    - 压缩存储镜像后发布
2. 参考
   - https://www.jianshu.com/p/c6cd257676bf
   - https://juejin.cn/post/6844903805578919949
   - https://blog.csdn.net/weixin_39620653/article/details/111656276

## qt-cmake-deploy
   - https://blog.csdn.net/weixin_39614657/article/details/112339834
