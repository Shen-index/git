# git

## 1.配置

​	打开终端>

​	name:

 				git config --global user.name "shen"

​	email

​				git config --global user.email "177623132@qq.com"

​	





## 2.使用git

- git status 
  - 查看当前仓库
- git init
  - 初始化仓库
- git log
  - 查看历史修改记录
- git  *
  - 把所有未追踪和已修改后的文件都变成暂存
- git commit -a -m “”
  - 提交所有已修改的文件，未跟踪的文件不会上传
  - -a:提交所有未修改

```html

```



刚刚添加到文件中的文件处于未跟踪状态

未跟踪 --->暂存

git add <filenmame> 将文件切换到暂存的状态（绿色）/没有存到仓库里

暂存 --> 未修改

git  commit -m "做了什么功能"  将暂存的文件存储到仓库中			

未修改 ---> 修改

​	修改代码以后，文件会变成修改状态





例如，咱在记事本修改了内容

​	先暂存 (git add 文件名)> 未修改 （git commit -m “做了什么功能”）





当咱添加了一个文件后

​	未追踪 （git *） > 暂存  git -commit -m "做了什么功能"



## 3.常用的命令

### 3.1.重置文件

- git restore  "文件名" ：  重置咱刚刚设置的文件
- git restore * :   把咱刚刚设置的所有文件都重置
- git restore --staged <filename> :取消暂存状态，不会取消操作，没了就是没了

### 3.2.删除文件

- git rm <filename>  :      删除
- git rm <filename>  -f  :强制删除

### 3.3.移动文件

- git mv from to #移动文件/重名命文件

## 4.分支（master）

git在存储文件时，它每一次代码提交都会创建与之对应的节点，git就是通过一个一个的节点来记录代码的节点，节点会构成树状结构，树状结构就意味着这个树会存在分支，默认情况下仓库只有一个分支，可以创建新的分支，和分支之间相互独立，意味着我在这边修改不会影响另外一边的分支节点

- git log                         #查看历史做的操作
- git branch                  #查看分支
- git branch   ”分支名“     #创建新分支
- git branch -d “分支名”  #删除分支
- git switch  ”分支名“      #切换到那个分支
- git  switch -c "分支名"   #创建并切换分支   





#### 4.1.注意：

- *当我们只有一个主分支，后面需要添加新的功能，*	

  - *那么咱就得创建新的分支*

    -   当我们提交代码后，也不会影响到主分支
    - 当我们再次提交代码后，就会在新的分支往后的主线上继续走

    - 

      因为咱如果在主分支上添加新内容，这个项目就会有问题*

      ​          *-当线上的项目出bug后，咱就得切换分支到主分支去改*

      ​            *- 需要改bug，那得在主分支中添加一个新的分支*

      ​            	*问题一*

      ​         		     *1.如果咱没有git控制版本改咋办*

      ​         	   *解决：那得把新的代码删完，删到添加name节点那里，再重新写* 

  

  

  - ​	accept current change  		保留前面的
    - accept incoming change 	 保留后面的
    - accept both changes 两个都保留

  

  - 合并完后，就可以把bug1删了
    - ​	git branch -d bug1




- 当我们在一家新的公司里，需要拿到公司的代码
  - 咱要先创建分支
  - 再在咱的分支进行开发,所以咱一定要在自己的分支上添加新功能

#### 4.1.0.分支

当我们在主分支创建的新分支修改完bug后，咱得让我们修改的新分支代码上线到主分支上去

- 合并分支
  - git merge bug1
- 当我们功能实现了后，就需要把咱敲的功能合并到主分支里头
  - git merge text
    - 问题一：它和咱之间合并bug1那个分支重复了
      - 解决：删其一，或者是全都要，总之，想要实现啥子效果就要哪锅

#### 4.1.1变基（rebase）

- 把分支原先的根变基到其他根上
  - git首先会找两个分支最近的祖先（根）
  - 对比当前分支分支和根发生了啥子变化（历史提交），将他们不同提取出来存储到一个临时文件
  - 将当前部分指向目标的基底
  - 以当前基底重新执行变基过来的那段分支的历史提交 





- 变基和merge对于合并最终都是一样的，不过变基的提交记录更加整洁
  - 大部分情况下，合并和变基都是可以互换的，但是如果提交到远程仓库了，不建议使用变基 
- 在开发中，我们除了通过merga来合并分支，还可以通过变基来合并
- 我们通过merga合并分支时，在提交记录中会将所有的分支合并的过程全都显示出来，这样项目比较复杂开发过程比较波折时，我必须要反复创建，合并，删除分支，这样一来就会使得代码提交记录变得很混乱



## 5.远程仓库

远程仓库可以被多人同时访问使用，方便咱共同使用，在工作中，git服务器一般由公司内部搭建，咱学习阶段，直接使用一些公共git仓库，，目前常用的有两锅，gitHub（远程git库），gitee（码云）

github操作

```pash
git remote add origin https://github.com/Shen-index/htmlcss.git
#git remote add <remote name> 后面跟地址

git branch -M main
#修改分支的名字为main

git push -u origin main
#git push 将代码上传到服务器上
```



gitee操作

```pash

git remote add gitee https://gitee.com/loser--shen/html.git
#git remote add <remote name> 后面跟地址

git push -u origin master
#git push 将代码上传到服务器上
```





## 6.远程库的操作

``` pash
git remote #列出当前的关联远程库

git remote add <远程库名> <url> #关联远程仓库

git remote remove <库名> #删除远程库

git push -u <远程库名> <分支名> #向远程仓库推送代码，并和当前分支关联

git push <远程库> <本地分支> <分支名> #在远程库中添加一个新的分支

git clone <url> #从远程下载分支（代码）

git clone <url> <name>#从远程下载d（代码）

git push #推送远程库

git fatch #从远程仓库下载所有代码，但它不会将代码和自己的分支合并
	#使用fatch拉取代码后，咱得手动将代码进行合并
	
git pull #从服务器自动拉取代码并自动合并


#如果本地库的版本低于远程库，push默认是推不上去的，
	需要推送，那么本地库和远程库版本一致
	
```



#在推送代码时，要先从远程库中拉取最新的代码

