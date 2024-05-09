#### 设置签名（用户名和邮箱）



![image-20240509141416729](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509141416729.png)



这里使用了全局设置，后续就默认为 Zhouyy 和 2176801587@qq.com 了

如果后续需要在某个特定的项目中使用不同的用户名或邮箱，则需要单独配置

git config user.name " 用户名 "

git config user.email " 邮箱 "



#### 初始化：

**git init 文件**

添加文件到暂存区（多个文件用空格分隔）

![image-20240509141815858](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509141815858.png)



#### 提交文件到本地库

**git commit -m "注释" 文件**

![image-20240509142705385](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509142705385.png)



#### 查看状态

**git status**

![image-20240509143209671](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509143209671.png)



修改文件demo.txt，再次进行查看：


![image-20240509143318842](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509143318842.png)

demo.txt被修改了，需要重新提交

git add demo.txt

git commit -m " ...... " demo.txt





#### git 日志

git log        由近到远操作记录

![image-20240509144236088](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509144236088.png)



当历史记录过多的时候，查看日志具有分页效果

下一页：空格

上一页： b

到尾页会显示end

退出：q



日志展示方式：

1. **git log**   ：                          展示详细信息

2. **git log --pretty=oneline**

3. **git log oneline**
4. **git reflog  :**                        HEAD@{数字}        数字含义：回退需要的步数



#### 版本回退：reset

1. **git reset --hard + 索引号**

(注意git里面不能直接使用ctrl+v，需要选中之后右键粘贴)

本地库回退的同时，暂存区和工作区同步回退

![image-20240509150158267](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509150158267.png)



2. **git reset --mixed + 索引号**

本地库回退的同时，暂存区也回退，工作区保持不变



3. **git reset --soft + 索引号**

本地库回退时，暂存区和工作区不变







#### 删除操作

**rm 文件名**        ——删除工作区文件

**git add 文件**          ——将删除操作同步到暂存区

**git commit -m " ... " 文件 **       ——将删除操作同步到本地库

**删除操作仍然可以通过git命令进行回退**





#### 对比文件差异

（用于确认各区域文件是否一致）

**git diff**

比较工作区与暂存区所有文件区别

**git diff 文件名**

比较工作区与暂存区具体文件区别

**git diff HEAD 文件名**

比较暂存区和本地库的区别

**git diff 索引号 文件名**

比较暂存区和本地库的历史区别



![image-20240509152049096](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509152049096.png)





#### 分支

##### 			1.查看分支

​		**git branch -v** 

![image-20240509153940689](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509153940689.png)



##### 				2.选择分支

​	

1. **创建分支**：**git branch 分支名**                            创建一个新的分支，但是不会切换到新的分支。
2. **查看分支**：**git branch**                                         列出所有的本地分支。当前活动的分支前面会有一个  *****  标记。
3. **切换分支**：**git checkout 分支名**                         切换到指定的分支。
4. **创建并切换分支**：**git checkout -b 分支名**        创建一个新的分支，并且立即切换到新的分支。
5. **查看所有分支**：**git branch -a**                              这个命令会列出所有的本地分支和远程分支。
6. **查看分支详细信息**：**git branch -v**                      显示每个分支的最后一次提交。



#### 别名

查看所有别名

**git remote -v**

![image-20240509195348288](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509195348288.png)



为地址取一个别名（origin）：

**git remote add 别名 地址**

![image-20240509195528327](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509195528327.png)



#### 推送

将master分支推送

(github上主分支应该是main)

git push 地址/别名 main

![image-20240509200451315](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509200451315.png)



#### 复制项目

克隆：

1. 初始化本地库
2. 将远程库内容完整克隆到本地
3. 创建远程库别名   **git remote add 别名 地址**

![image-20240509200901642](C:\Users\Yiyun\AppData\Roaming\Typora\typora-user-images\image-20240509200901642.png)



#### 拉取项目

pull = fetch + merge

1. 先确认远程库内容是否更新
2. 抓取操作：
   - git fetch 项目地址或别名 main
     - 只是将远程库下载到本地，但是工作区没有任何更新
   - 抓取后可以去远程库查看内容是否正确
     - 切换远程库：       **git checkout 地址或别名/ main**
     - 查看文件         ： **cat 文件**
   - 合并
     - **git merge 地址或别名/main**

3. 直接拉取
   - **git pull origin master**





#### 发送推送失败： 

发生冲突的情况下，应该先拉取下来，然后修改冲突，最后进行推送





