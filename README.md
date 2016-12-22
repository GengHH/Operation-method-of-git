# Operation-method-of-git
The most common Operation method of the tool about git.The purpose is convenient reference.

**markdown** 的标记语法

**这篇文章介绍的是若何利用git bash 工具实现最常用的git相关的操作方法，从而实现和github的联合使用。**

##第一种情况(克隆别人的项目再提交到自己的github仓库)
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
  
###9.以上步骤结束后，首先执行以下的某条命令（目的是在远程仓库发生改变后，实现本地仓库和远程仓库同步更新）
  命令：
  
    
     更新当前分支
    
     >$ git pull 
     
     or更新 origin remote 的 master 分支
    
     >$ git pull origin master
     
     or获取服务器端的改动，比如其他用户新建了一个分支并push到了服务器，运行这个命令之后会得到这个分支的信息
     
     >$ git fetch
   

###10.若果想要将该项目提交到自己的github的新建的repertory中，使用远程推送
  命令：
  
    >$ git push  git@github.com:GengHH/***.git
  
  git@github.com:GengHH/***.git 代表自己的github仓库的地址




##第二种情况（将本地的以项目首次上传到自己的github上）

*注意：* **前提是建立好了公钥和私钥。本地和远程github服务器能够连通**

###1.在myProject根目录下执行 git init，把工程转化成git工程。
  	$>git init

###2.在myProject根目录下配置提交的用户名和mail地址
	$>git config --global user.name "myname"  
	$>git config --global user.email "mymail@mymail.com"  

  提醒：**该步骤并不是必须的**

###3.在myProject根目录下执行：
	$>git remote add origin https://github.com/myname/***.git


###4.在本地仓库中添加该项目的所有的内容
	$>git add .

   提醒：**可以根据git add <文件名>有选择的添加内容**

###5.提交该项目到本地仓库

	$>git commit -m "first commit"  

 提醒：**-m后面跟的是提交时的备注**

###6.更新本地仓库的master分支使得和远程master分支保持一致
	$>git pull --rebase origin master

###7.推送本地仓库到远程仓库
	$>git push -u origin master
	
 提醒：**之后的推送只需要执行 git push即可**
