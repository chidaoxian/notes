# git与npm相关的一些问题（持续更新）

秋招后的一些记录，看了很多东西想写下来，希望自己可以随时的查看，也希望有错误的地方大神可以指正。

# git

其实感觉git很简单，看文档全部理解透彻点，这里主要是记录一下被问到过的问题，其实我一般在开发中真的可能比较依赖idea的那种图形化的处理方式，主要是比较清晰与准确吧。

## 1、版本回退

### 主要步骤

（1）git log 查看版本信息

（2）git  reset 返回该版本

### git  reset

（1）git reset --hard xxx

​		git reset --hard HEAD^（撤销前前一次 commit）

​		git revert HEAD（撤销前一次 commit）

​		将最近一次提交节点的提交记录全部清除

（2）git reset --soft xxx

​		将最近一次提交节点的提交记录回退到暂存区

（3）git reset --mixed xxx

​		将最近一次提交节点的提交记录回退到工作区

### git reflog

该命令用来记录你的每一次命令

## 2、合并分支

（1）git  checkout master

（2）git  merge dev

（3）将某分支的某次提交合并到另一分支

​		git cherry-pick

​		代码开发的时候，有时需要把某分支（比如develop分支）的某一次提交合并到另一分支（比如master分支）

​		步骤：1、切换dev分支，git log 获取版本id。2、切换到master分支，使用git cherry-pick 版本id  ，就把该条commit记录合并到master分支。

## 3、fetch和pull的区别

### fetch

相当于是从远程获取最新版本到本地，但不会自动 merge

### pull

相当于是从远程获取最新版本并 merge 到本地

### git pull

命令其实相当于 git fetch + git merge

# npm

这边简单的总结一下被问到过的问题。

## 1、npm的介绍

### npm安装

当我们在安装 node 后，npm 也会一起安装好

### npm命令

1、npm init：npm init 命令用来初始化项目

2、npm install：npm install  命令用来全局安装或本地安装第三方的依赖

3、npm view(info)：npm view(info) xxx ,查看包 xxx 的一些信息，最新稳定版本，在线压缩包地址，依赖等信息。

4、npm home(docs) xxx ，都会打开在线 github 地址，前提需要在包 xxx 的 package.json 文件中设置 homepage 字段

5、npm repo(bugs) xxx, 跳转到对应的 github repo页面，前言也是需要配置

6、 npm ls：显示依赖 tree

### package.json

一个项目的全部信息都在 package.json 文件中了

### npx

npx 可以帮我们直接执行 node_modules/.bin文件夹下的文件

### npm发布

首先使用 nrm 切换到 npm 官方源
使用 npm login 进行登录（提前注册）
npm publish (确保 name 是唯一值)
对于不想打包的可在 .npmignore 文件中进行忽略

## 2、请问 package.json 中版本 ~1.2.3和^1.2.3 有什么区别？

1、字符范围：X.Y.Z  -  A.B.C

2、Tilde Ranges : ~
如果Y被指定，则允许Z被改变；如果没有，允许Y被改变

~1.2.3 , Y 被指定为 2, 那么匹配的范围为 >=1.2.3 <1.3.0
~1.2, Y 被指定为 2, 那么匹配的范围为 >=1.2.0 <1.3.0
~1, 没有指定 Y, 那么 Y 可以被改变，匹配的范围为 >1.0.0 <2.0.0

3、Garet Range: ^

（1）匹配的版本，会保证最左边的第一个非 0 位不修改

（2）^1.2.3, 最左边非 0 位为 X 位，所以匹配的范围为 >=1.2.3 <2.0.0

（3）^0.2.3, 最左边非 0 位为 Y 位，所以匹配的范围为 >=0.2.3 <0.3.0

（4）^1.2.x , 当版本缺失，缺失位会降到 0 ，所以匹配的范围位 >=1.2.0 <2.0.0

## 3、npm install 如何工作 —— node_modules 目录结构

### npm2

**npm 2 在安装依赖包时，采用简单的递归安装方法。**

依赖关系层层递进，构成了一整个依赖树，这个依赖树与文件系统中的文件结构树刚好层层对应

1、对复杂的工程, node_modules 内目录结构可能会太深，导致深层的文件路径过长而触发 windows 文件系统中，文件路径不能超过 260 个字符长的错误。

2、部分被多个包所依赖的包，很可能在应用 node_modules 目录中的很多地方被重复安装。随着工程规模越来越大，依赖树越来越复杂，这样的包情况会越来越多，造成大量的冗余。

### npm3 - 扁平结构

**npm 3 扁平化管理, 在安装时遍历整个依赖树，计算出最合理的文件夹安装方式, 避免重复安装**

### npm 5 - package-lock 文件

1、这一版本依然沿用 npm 3 之后扁平化的依赖包安装方式，此外最大的变化是增加了 package-lock.json 文件。

2、package-lock.json 的作用是锁定依赖安装结构。

3、如果查看这个 json 的结构，会发现与 node_modules 目录的文件层级结构是一一对应的。

4、只要有这样一个 lock 文件，不管在那一台机器上执行 npm install 都会得到完全相同的 node_modules 结果。

## 4、npm和yarn的区别

**Yarn 是为了弥补 npm 的一些缺陷而出现的**

速度快 ：

1、速度快 

2、离线模式：如果之前已经安装过一个软件包，用Yarn再次安装时之间从缓存中获取，就不用像npm那样再从网络下载了。

安装版本统一：Yarn 有一个锁定文件 (lock file) 记录了被确切安装上的模块的版本号（yarn是默认生成的）。

3、更简洁的输出。

4、更好的语义化。