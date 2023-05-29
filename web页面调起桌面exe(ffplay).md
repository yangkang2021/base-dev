# web页面调起桌面exe(ffplay)

## 第一步：写注册表
把下面代码保存到文件ffplay_chrome.reg然后管理员模型运行
```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\ffplay]
@="ffplayProtocol"
"URL Protocol"=""
 
[HKEY_CLASSES_ROOT\ffplay\DefaultIcon]
@="E:\\tools\\ffmpeg\\ffplay_chrome_wrapper.exe,1"
 
[HKEY_CLASSES_ROOT\ffplay\shell]
 
[HKEY_CLASSES_ROOT\ffplay\shell\open]
 
[HKEY_CLASSES_ROOT\ffplay\shell\open\command]
@="\"E:\\tools\\ffmpeg\\ffplay_chrome_wrapper.exe\" \"%1\""
```

## 第二步：编写ffplay_chrome_wrapper.exe处理参数
- argv[0] 是exe
- argv[1] 是定义的协议，参数里面不能有空格，比如：ffplay://参数1,参数2
- 处理目的：去掉头（ffplay://），支持多参数拆分
```
#include <iostream> 
#include <string>

using namespace std;
int main(int argc, char* argv[])
{
	if (argc < 2) return -1;

	string url =  string(argv[1]); 

	string r = "://";

	string args = url.replace(url.find_first_of(r), r.length()," "); //只是去掉头，不支持多参数拆解
	system(args.c_str());
	return 0;
}
```

## 第三步：web页面调起exe
```
<html>
	<body>
		<a href="ffplay://https://xxx.ts"> 点击使用ffplay播放视频 </a>
	</body>
</html>
```
## 参考：https://www.freesion.com/article/8630491343/