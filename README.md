# 一. 简易git使用教程
```
Attention:如果你是刚接触git及gitlab,该文档能帮助你快速上手
```
老鸟请直接跳转阅读[使用规范(必读).md](使用规范(必读).md)
## 1.1 参照资料：
1. [git简易使用手册](https://www.bootcss.com/p/git-guide/)
2. [git官网使用手册](https://git-scm.com/book/zh/v2)
    
## 1.2 看完教程后你可以常识做下以下练习
TodoList:

    1. 安装git客户端（windows下载git.exe安装）
    git.exe客户端：https://git-scm.com/download/win
    非开发人员可使用TortoiseGit图形界面： https://tortoisegit.org/download/
    
    2. 本地设置user.email及user.name配置（鼠标右键gitbash here）
     （git config --global user.name 邮箱前缀     举例：git config --global user.name eric.xi
       git config --global user.email 个人邮箱 git config --global user.email eric.xi@xxx.com）
    
    3. 生成ssh密钥对，上传公钥到gitlab 
        (a. 本地git客户端  ssh-keygen -t rsa产生密钥对， 
        b. isa.pub文件内容复制到gitlab密钥对)
        
    4. 克隆当前仓库，切换到dev分支，基于dev分支创建自己的分支
    分支命名为dev_xxx,  xxx为自己英文名
    如james则创建dev_james
    
    5. 切换到自己的分支，在name_files目录下创建以自己英文名命名的文件，提交，推送。
    
    6. 在gitlabs上发起merge request，从自己分支合并到dev分支。
    
    7. 设置推送当前分支到远端同名分支， git config --global push.default current

# 二. svn已有仓库迁移gitlab操作
## 2.1 step1: 克隆svn代码

```git svn clone svn项目地址 --authors-file=users.txt```

users.txt文件中存放svn账号与gitlab账号对应关系，=左侧为svn账号，右侧为git账号

users.txt示例如下:

```
kevin=kevin.he<kevin.he@xxx.com>
Bob=bob.xiang<bob.xiang@xxx.com>
michael.yin=michael.yin<michael.yin@xxx.com>
jesse.xu=jesse.xu<jesse.xu@xxx.com>
```

## 2.2 step2: gitlab创建项目
项目放入对应的group下，目前已有group为swa及dp

## 2.3 step3: 推送本地仓库到gitlab
```
cd 仓库目录
git remote add origin 远端仓库地址
git push
```

**git常用命令清单：**更多指令请查看[git常用指令清单.md](git常用指令清单.md)

| git命令 | 作用 |
| ------ | ------ |
| git config --global push.default current | 设置推送当前分支到远端同名分支 |
| git status | 查看当前仓库状态 |
| git branch -a | 查看所有分支 |
| git remote -v | 查看远端仓库配置 |
| git add . | 本地变更加入到暂存区 |
| git commit -m "bug修复-接口xx报错" | 提交本地修改到本地仓库 |
| git pull | 拉取远端变更到本地 |
| git remote -v | 查看远端仓库配置 |
| git status | 查看当前分支状态 |
| git push | 推送当前分支变更到远端 |



# 三. 分支管理策略
![分支管理策略](./git-model.png)