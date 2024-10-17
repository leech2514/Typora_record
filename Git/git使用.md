# git使用历史总结

## git bash中提交文件

- 在文件资源管理器里
- 别忘了指定分区
- 文件提交流程
  -   git add . 
  - git status
  - git commit -m "file_name"
  - git push

## idea中固定文件提交至指定分支

注意：更改提交分支为找到右下角的分支，在分支的下一级选项中有==签出==，点击该选项更改要提交到的分支



# 项目创建

`在项目创建时，使用git和远程控制github,以及idea有部分区别`

## 用github远程控制

1. 先在github中 create a new repository，并填写好相关信息。注意添加READEME file

2. 在本地创建一个存储代码的文件，在本文件夹内打开git bash

3. 接着在git bash中输入相应的git命令，如设置用户名、设置邮箱、文件提交等

4. 从已经创建的项目中，clone出来HTTPS,使用`git clone 具体的https地址`，将项目clone到本地

5. 若idea为配置git，在VSC选项中选择集成，再选择相应的集成工具git即可，若有其他配置再接着操作就完了

6. 可以在git bash中通过git命令提交，也可以在idea中进行提交等操作

   

分支？如何理解和操作？

<u>详细解释见涤生Java SE 阶段的git&Maven文档</u>

****

****

# 常用的git命令

1. 配置用户名:`git config --global user.name wkx`
2. 配置邮箱：`git config --global user.email 3430928190@qq.com`
3. 从github下载项目，初始化：`git clone 项目链接`；项目文件中的.git文件包含的是版本控制的相关文件，不需要去操作
4. 自己创建项目：先创建文件夹，打开文件夹并在文件夹内打开git bash，然后在git bash中输入`git init`进行初始化，用于创建.git文件。接下来是自己去编写项目，编写完成后进行代码管理。接下来提交已将编写好的代码，先输入命令`git add .`，此处的`.`是当前文件夹的意思，该命令的意思是让git将该文件夹内的所有文件和非空文件设置为准备提交的状态（暂存区），如果想提交特定文件，使用命令`git add  具体文件名`。再输入命令`git commit -m "xxx"`进行提交，此处的`“xxx”`是对该次提交的备注，提交成功后git会把源代码以数据库的形式保存在仓库中，可以用`git log`查看提交的历史记录。
5. 查看提交历史记录：`git log`
6. 代码恢复：`git checkout HEAD main.py`；从最后一次的提交里，把main.py复制到工作区（会覆盖）
7. 查看当前状态：`git status`



1. 创建分支：`git branch branchName`
2. 切换分支：`git checkout branchName`
3. 创建分支同时切换到新分支：`git checkout -b newBranch`;相当于1和2两条命令的执行结果；
4. 查看所有分支：`git branch -a`
