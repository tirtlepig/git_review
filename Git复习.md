# Git复习

## 一、版本控制

## 二、git vs svn

git是分布式版本控制，svn是集中式版本控制，svn工作结束后需要提交到中央服务器，而git不需要联网是保存在自己的电脑上，联网后再push。

## 三、git环境配置
git bash：Linux风格命令行
git cmd：windows风格命令行
git gui：图形界面git

## 四、linux基本命令

1. cd：改变目录

2. cd..回退到上一目录，直接cd回退道默认目录

3. pwd：显示当前所在的目录路径

4. ls（ll）：列出当前目录包含的所有文件，ll列出的更加详细

5. touch：新建一个文件 后面要带文件名和后缀

6. rm：删除一个文件，rm index.js

7. mkdir：新建一个目录即文件夹

8. rm-r：删除一个文件夹 rm-r src 删除src文件夹

9. mv 移动文件 mv +文件+目标文件夹 需要保证目标文件夹和文件在同一目录下

10. reset 清屏 重新初始化终端

11. clear 清屏

12. history 查看历史命令

13. help帮助

14. exit推出

15. #表示注释

## 五、git配置
1. git config -l 查看配置
2. git config --system --list 查看系统配置
3. git config --global --list 查看用户配置
4. 设置用户名 git config --global user.name "xxx"
5. 设置邮箱 git config --global user.email xxx
## 六、git 基本理论

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7Ksu8UlITwMlbX3kMGtZ9p0NJ4L9OPI9ia1MmibpvDd6cSddBdvrlbdEtyEOrh4CKnWVibyfCHa3lzXw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### ![git-repo](https://www.liaoxuefeng.com/files/attachments/919020037470528/0)

## 七、git版本控制的一些命令

### 7.1常用
1. git init 创建仓库
2. git status查看当前仓库状态
3. git diff 查看difference（具体修改的内容） 如：git diff readme.txt ，git diff HEAD -- readme.txt命令可以查看工作区和版本库里面最新版本的区别
4. git add<filename>把文件添加到仓库
5. git commit -m+信息 将文件提交到仓库

### 7.2关于版本回退 

1. git log 显示最近到最远的提交日志，如果输出信息过多可以添加 --pretty=oneline参数
2. 在Git中，用`HEAD`表示当前版本在Git中，用`HEAD^`表示当前版本上上一个版本就是`HEAD^^`  如git reset--hard HEAD^
3. git reset -hard+ comit id/HEAD^等
4. git reflog记录每一次命令

### 7.3关于修改

1. git diff 查看difference（具体修改的内容）git diff HEAD ---------见上

2. git checkout --file 丢弃工作区的修改（注意说工作区中的），还需要注意的是此命令区别于git checkout（不带--）这是切换到另一个分支的意思，见后

3. git reset HEAD file可以将暂存区的修改撤销，重新放回工作区，（实际试验是不加文件名的话会将所有的文件全部撤销）

   （我也不知道为啥那是个PS，可能是powershell的意思吧）

   ![image-20220111194216243](C:\Users\86184\AppData\Roaming\Typora\typora-user-images\image-20220111194216243.png)

4. git checkout其实是用版本库中的版本替换工作区中的版本

## 八、远程仓库
### 8.1远程仓库

本地git仓库与GitHub之间的传输通过ssh加密，所以要做如下设置

配置过程见廖雪峰老师教程：[远程仓库 - 廖雪峰的官方网站 (liaoxuefeng.com)](https://www.liaoxuefeng.com/wiki/896043488029600/896954117292416#0)

