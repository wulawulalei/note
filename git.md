## .git文件

hooks		目录包含客户端或者服务器的钩子脚本

info			包含一个全局排除文件

logs			保存日志信息

objects		目录存储所有的数据内容

refs				目录存储指向数据（分支）的提交对象的指针

config			文件包含项目特有的配置选项

description	用来显示对仓库的描述信息

head			文件指示目前被检出的分支

index			文件保存暂存区信息



## git命令

git status

作用：查看文件的状态

命令：git status

红色表示工作区中的文件需要提交

绿色表示暂存区中的文件需要提交

 

git add .

作用：将未追踪的文件添加到暂存区(先将工作目录中的修改做成git对象放到版本库再从版本库提出git对象放到暂存区)

git ls-files -s  查看暂存区

git add 文件路径

git add -A | git add --all | git add .	将所有未追踪的文件都提交到暂存区

 

git commit

作用：将暂存区的所有文件提交到本地仓库

git commit -m “”

 

git log

作用：可以帮助我们查看提交日志

git log--oneline://查看简洁日志，会在地行显示日志信息

git reflog//获取所有操作的日志，包含回退的版本号



> git log和git reflog的区别为

1. git log命令是显示当前的`HEAD`和它的祖先
2. git reflog可查看到所有历史版本信息

 

git clone “项目地址”

作用：拷贝一份远程仓库，也就是下载一个项目。

 

git branch/git branch “分支名字”

作用：查看所有分支/创建分支

 

git checkout “分支名字”

作用：转换当前分支

 

git push

作用：上传远程代码

 

git pull

作用：下载远程代码

 

git stash

作用：将当前工作区的内容保存



git stash show

作用：显示做了哪些改动



git  stash apply

作用：应用某一个存储，但不会把存储从存储列表中删除



git stash pop

作用：回复之前的工作目录



git merge “branch-name”

作用：j将branch-name分支合并到当前分支



git diff

作用：查看哪些更新没有暂存(加上--cashed为查看哪些更新暂存完没有提交到本地)




git reset --hard

作用：彻底回退到某个版本，本地的源码也会变为具体版本的内容，撤销的commit中所包含的更改被冲掉


git reset --soft

作用：回退到某一个版本，只回退了commit信息，源码内容不变

git reset HEAD .撤销已经add的文件






git cherry-pick commitHash

作用：将其他分支的commit合并到另外一个分支，也就是在当前分支末尾增加了此commit

1. 合并一两个commit

   ```
   git cherry-pick <HashA> <HashB>
   ```

2. 合并A和B两个commit之间的提交(不包含A提交，要包含A提交则要在A后加上^)

   ```
   git cherry-pick A..B
   ```




git cherry-pick --continue

作用：用户解决代码冲突后，第一步将修改的文件重新加入暂存区（`git add .`），第二步使用下面的命令，让 Cherry pick 过程继续执行。


git cherry-pick --abort

作用：发生代码冲突后，放弃合并，回到操作前的样子。


git cherry-pick --quit

作用：发生代码冲突后，退出 Cherry pick，但是不回到操作前的样子。


git revert commitHash

作用：回滚某一次commit



git rebase master

作用：执行操作时，会先找到两个分支的共同祖先，然后提取当前分支上的修改，并将当前分支指向master分支的最新提交，最后将刚才提取的修改应用到master分支最新提交的后面（这个过程会删除原来当前分支的修改，生成新的修改，也就是删除原来的C、D，生成新的C、D）



## push

git的push流程是比对commit记录，把本地多出的代码给提交上去



## 基础的linux命令

clear	清除命令

echo "text"	往控制台输出信息

ll	将当前目录下的子文件和子目录平铺在控制台

find 目录名	将对应目录下的子孙文件和子孙目录平铺在控制台

find 目录名 -type f	将对应目录下的文件平铺在控制台

rm 文件名	删除文件

mv 源文件 重命名文件	重命名文件

cat 文件的url	查看对应文件的内容

vim 文件的url	进入文本

- 按i进入插入模式，进行文件的编辑
- 按esc退出插入模式
- 按：进行命令的执行
  - q!	强制退出
  - wq  保存退出
  - set nu  设置行号



commit命名规范：

- feat：新增功能
- fix：bug 修复
- docs：文档更新
- style：不影响程序逻辑的代码修改(修改空白字符，格式缩进，补全缺失的分号等，没有改变代码逻辑)
- refactor：重构代码(既没有新增功能，也没有修复 bug)
- perf：性能, 体验优化
- test：新增测试用例或是更新现有测试
- build：主要目的是修改项目构建系统(例如 glup，webpack，rollup 的配置等)的提交
- ci：主要目的是修改项目继续集成流程(例如 Travis，Jenkins，GitLab CI，Circle等)的提交
- chore：不属于以上类型的其他类，比如构建流程, 依赖管理
- revert：回滚某个更早之前的提交





git中一个文件对应一个git对象





### commit

- 当commit后发现有内容忘记add的时候，可以把忘记的内容先add了再使用amend合并到上一个commit.

```
git commit --amend --no-edit
```

- 当commit后发现commit信息要修改时，使用amend进入到修改信息，键入:i可进行编辑，键入:wq保存并退出

```
git commit --amend
```



### checkout

- 当文件放进暂存区后，不小心改到放进暂存区的文件时，则可以使用checkout将工作区的指定文件的内容恢复到暂存区的状态

```
git checkout filename
```

