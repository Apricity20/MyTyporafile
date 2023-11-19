## ==git使用==

[git官网](https://git-scm.com/)

[知乎git与github使用介绍1](https://zhuanlan.zhihu.com/p/369486197)



git是分布式版本控制软件

<img src="D:\1.Study\Typora\picture\image-20231117122805308.png" alt="image-20231117122805308" style="zoom:33%;" />

### 一、git指令

#### 1.git基本操作

1. git init 初始化文件夹，用git将文件夹管理起来之后。会生成一个.git的隐藏文件夹包含配置信息
2. git status 检测当前文件夹里的文件状态
3. git add hit.txt 将指定文件夹管理起来
   git add . 管理所有未管理的文件
4. git commit -m 'v1' 提交一个版本，此时已经生成了第一个版本
   将文件内容修改后再次检测状态，发现修改
   git add . 对文件进行管理
   git commit -m 'v2' 此时生成第二个版本
   git log 查看版本迭代信息

#### 2.个人信息配置，用户名，邮箱

1. git config -global 

==**git三大分区（工作模式）**==

<img src="D:\1.Study\Typora\picture\image-20231117160254872.png" alt="image-20231117160254872" style="zoom:33%;" />



#### 3.回滚版本

- 回滚到之前的版本

```
git log 版本提交
git reset --hard 版本号
```




- 回滚到之后版本

```
git reflog 回滚的记录
git reset --hard 版本号
```

<img src="D:\1.Study\Typora\picture\image-20231117173131934.png" alt="image-20231117173131934" style="zoom: 200%;" />

```
git checkout -- 文件名 清楚变动
```



## 二、git分支的概念

涉及到存储容量的问题，不同版本之间指出不同之处

项目有一个主分支，为协同工作开发新功能，可以基于当前版本创建新的分支

两个基于同一主分支的分支如果改动不在同一行的话，可以自动合并成功。否则，需要手动解决冲突

#### 1.分支操作

```
git branch 查看分支
git branch dev 创建新的分支
git checkout dev 切换当前工作到分支
git checkout master 不同分支下文件内容是隔离的

```

```
git branch -d
git branch -D 删除分支
```

- 查看分支

```
git branch
```

#### 2.合并分支到主分支

```
git merge bug 在主分支下合并bug分支
git branch -d bug 删除无用的bug分支
回到dev分支继续开发完成
git checkout master
git merge dev
```

此时发现合并冲突，git将两个文件不同的内容放出来。需要找到文件手动解决冲突

#### 3.工作流

开发都要创建新的分支，等到功能完善后再进行主分支的合并



## 三、github云托管

github与git没有直接关系，git是本地管理工具，github,gitlab是代码云托管==仓库==

1. 给远程仓库起别名

   ```
   git remote add origin https://github.com/Apricity20/demo1.git
   ```

2. 向远程推送代码

   ```
   git push -u origin 分支
   ```

3. 克隆远程仓库代码第一次

   ```
   git clone 远程仓库地址
   ```

4. 切换分支

   ```
   git checkout 分支
   ```


在公司进行开发

```
1.切换到dev分支进行开发
	git checkout dev
2.把master分支合dev[仅一次]
	git merge master
3.修改代码
4.提交代码
	git add .
	git commit -m
	git push origin dev
```

回到家中继续写代码

```
1.切换到dev分支进行开发
	git checkout dev
2.拉代码
	git push origin dev
3.继续开发
4.提交代码
	git add .
	git commit -m
	git push origin dev
```

到公司继续开发

开发完毕，要上线

```
1.将dev分支合并到master，进行上线
	git checkout master
	git merge dev
	git push origin master
2.把dev分支也推送到远程
	git checkout dev
	git merge master 将dev与master保持相同，方便下次开发
	git push origin dev
```



fenzhi



## 小问题

使用git log后出现无法输入的问题 按q回车

git与github远程推送时报错，https://blog.csdn.net/m0_64288219/article/details/127405426跳出一个系统认证，确认后github通过验证可以正常推送。这个方式经过验证可行

![image-20231117224549631](D:\1.Study\Typora\picture\image-20231117224549631.png)

```
cd demo1/ 到当前文件夹目录下
cat 111.txt 浏览指定文件
```

```
ls 查看当前分支内的文件
```

```
pwd 查看当前文件夹
```

```
touch a2.py 在当前分支下创建新的文件
```

