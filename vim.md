# vim的使用

## 一. 配置
set number
echo "set nu" >> ~/.vimrc && cat  ~/.vimrc


## 二. 跳转到行
1. 命令行模式下输入（n为指定的行号）：
    - （1）ngg / nG
    - （2）:n
    - （3）vim +n filename（注意这里要输入 + 号）
    三者的区别在于，ngg/nG输入以后不需要按下回车键，而输入:n之后还要按下回车键才会跳转，vim +n filename只能在打开文件时跳转到相应的行。
1. 比如想跳转到文本的第12行，可以执行如下命令：
    - （1）12gg / 12G
    - （2）:12
    - （3）打开文件时输入vim +12 filename
1. 文本中想查看当前行信息，可输入： Ctrl + g
1. 跳转到文首/文末:若在Insert模式下，需要先按一下Esc，
   - 文首：按gg（区分大小写）
   - 文末：按G（区分大小写）
1. 跳转到行首/行末
   - 行首：①按Home  ②按0（数字0）
   - 行尾：①按End   ②按$（Shift + 4）
1. 跳转到指定列
   - 输入 n| 或 0n| 命令（0 代表数字0，n 代表行号，| 代表竖杆符号）
   
## 三. 搜索
![](.images/70295514.png)
https://www.yiibai.com/vim/vim_searching.html

