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

### 8.2提交远程仓库
GitHub给予的提交方法：

![image-20220111222425338](C:\Users\86184\AppData\Roaming\Typora\typora-user-images\image-20220111222425338.png)

1. 要关联一个远程库：使用git remote add origin git@server-name:path/repo-name.git；
2. origin是默认习惯命名，关联远程库时要给远程库指定一个名字
3. 关联后的使用git push -u origin master第一次推送master分支的所有内容
4. 每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改

### 8.3从远程库克隆
git clone +git库地址 如：git clone git@github.com:michaelliao/gitskills.git（这不是我的）

## 九、分支管理

​		分支在实际中有什么用呢？假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。

​		现在有了分支，就不用怕了。你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。

### 8.1创建和合并分支
1.创建和合并分支的具体内容见廖雪峰老师博客：https://www.liaoxuefeng.com/wiki/896043488029600/900003767775424
2.HEAD严格的说指向的不是提交而是当前分支
3.创建分支命令，如创建dev分支：git checkout -b dev  checkout加-b参数 表示创建并切换，相当于：git branch dev+ git checkout dev
4.git branch 查看当前分支 会列出所有分支 当前分支前会标出*号
5.将一分支的工作成果合并到另一分支，如当前在master分支，将dev分支工作合并到master分支上 git merge dev
6.创建并切换分支的另一个命令 git switch -c dev，只切换分支 git switch xxx 更科学
7.git branch -d dev 删除dev分支
8.git merge的fast-forward模式：快速模式，直接改变master的指向，但不是所有的合并都能用这种方式

### 8.2冲突和冲突解决

![git-br-feature1](https://www.liaoxuefeng.com/files/attachments/919023000423040/0)

像这种在两个分支上都做了修改，试图将各自修改合并就会冲突，需要手动解决冲突然后再合并分支。

### 8.3分支管理策略
1.fast forward模式删除分支后会丢掉分支信息
2.强制禁用fast forward模式使用 git merge --no--ff -m+info +barchname  带-m参数是因为，本次合并要创建一个新的commit
#### 8.3.1分支策略
1.合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。
2.master上不应做开发，应该像图片所示：

![git-br-policy](https://www.liaoxuefeng.com/files/attachments/919023260793600/0)



