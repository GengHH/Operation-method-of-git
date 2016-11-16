# Operation-method-of-git
The most common Operation method of the tool about git.The purpose is convenient reference.

**markdown** 的标记语法

**这篇文章介绍的是若何利用git bash 工具实现最常用的git相关的操作方法，从而实现和github的联合使用。**

##第一种情况
### 1.首先在本地创建文件夹（也就是本地的git仓库）
   命令：
   
    >$ mkdir name_repo
    >$ cd name_repo
    
###2.再克隆github上的其他项目到本地仓库
   命令：
   
    >$ git clone gituser@git.server.com:project.git
###3.进行该项目的修改操作（比如添加一个文件 node.txt）
    //node.txt
     "这是刚添加的文件内容"
     
###4.查看此时的git状态  
   命令：
   
   >$ git status -s
   
   结果会显示如下：
   ?? node.txt
   显示问号的原因：Git是显示文件名前的问号。显然，这些文件不属于Git，Git 不知道该怎么用这些文件
   
###5.添加文件(node.txt)到存储区域，在使用 git status -s查看git的状态命令将显示文件暂存区域。
   命令：
   
   >$ git add node.txt
   >$  git status -s
   
   结果显示如下：
   
   A node.txt
   
###6.提交更改 (使用-m指令，后面直接跟上提交时的描述信息)
   命令：
   
  >$ git commit -m 'first commit'
   
   
###7（不必须操作）.提交后查看日志信息
  命令：
  
  >$ git log
  
  结果显示该项目的所有的提交的情况，按照时间先后排序显示，如
  
  commit 19ae20683fc460db7d127cf201a1429523b0e319
  
  Author: user name <*******.com>
  
  Date: Wed Sep 11 07:32:56 2013 +0530
  
  提交后查看日志信息，他使用 git 日志命令。它会显示提交ID所有提交的信息，提交作者，提交日期和提交的 SHA-1散列。
  
###8（不必须操作）. 使用git show命令查看提交的细节。 Git的show命令的SHA-1提交ID作为参数。
  命令：
  
  >$ git show 19ae20683fc460db7d127cf201a1429523b0e319
  
  结果会显示详细的修改情况，如：
  commit 19ae20683fc460db7d127cf201a1429523b0e319
  
  Author: user name <*******.com>
  
  Date: Wed Sep 11 07:32:56 2013 +0530
  
  +++ "这是刚添加的文件内容"
  
  三个+代表的是此次修改所新添加的文件内容
  
###9.以上步骤结束后，若果想要将该项目提交到自己的github的新建的repertory中，使用远程推送
  命令：
  
  >$ git push  git@github.com:GengHH/***.git
  
  git@github.com:GengHH/***.git 代表自己的github仓库的地址

