# 同步Overleaf, Github与本地latex文件

最近要用Latex多人协同写论文，于是就选了[Overleaf ](https://www.overleaf.com?r=d0e1bbd0&rm=d&rs=b)。这个网站可以实现多人协同写论文，并且支持latex在线编译，以及不同历史版本之间的diff，算是非常好用的latex在线编辑器了。唯独有个缺点就是编译太慢了，有时候大一点的论文还会报Time out错误。当然，氪金可以解决这个问题，不过像我这种苦逼的程序猿根本没钱去氪。于是，便想出了一个本地编译，同步到Overleaf上的法子，这就是借助github作为中间跳板，把本地，Overleaf和Github的仓库连起来。

## Overleaf与Github连接


![Overleaf界面](https://github.com/xurongxiang/Overleaf_to_GitHub/blob/master/fig/1.png)

打开Overleaf中的latex项目，我们现在的目标是把这里的项目同步到github上。
首先在左上角有个**Menu**,点它，可以看到许多关于项目的设置，我们如图找到github，点进去，按照提示一步一步操作（部分用户可能要收费，但是如果之前邀请过用户，那么就可以免费使用）


![找到github](https://github.com/xurongxiang/Overleaf_to_GitHub/blob/master/fig/2.png)


等把Overleaf里的项目同步到github里后，效果如图所示：



![Github里的项目](https://github.com/xurongxiang/Overleaf_to_GitHub/blob/master/fig/3.png)


在Github里就会有一个和Overleaf里项目内容相同的仓库。

## 连接Github与本地
这个其实就是Git的基本用法，这里还是详细示范一次吧。
首先本地新建一个文件夹，比如我建一个“paper”文件夹。


![空文件夹](https://github.com/xurongxiang/Overleaf_to_GitHub/blob/master/fig/4.png)


打开Git bash（没有的话，可以去下载一个）


![在这里插入图片描述](https://github.com/xurongxiang/Overleaf_to_GitHub/blob/master/fig/11.png)

然后输入

> git init

然后把github上的项目clone下来，比如以https://github.com/ruanlibuaa/OverleafGithubSynTest.git
这个项目为例，输入
>git clone https://github.com/ruanlibuaa/OverleafGithubSynTest.git

此时本地文件夹里就会有Overleaf上的项目了。


![如图](https://github.com/xurongxiang/Overleaf_to_GitHub/blob/master/fig/5.png)
 然后添加远程库，

>  git remote add origin https://github.com/ruanlibuaa/OverleafGithubSynTest.git


此时我们就连好了Overleaf，Github和本地了。
下面开始试用：
## Overleaf上的更新同步到GitHub上
Overleaf中改动后，还是点Menu中的github，会出现下面这个框，我们选择push到github上：

![同步](https://github.com/xurongxiang/Overleaf_to_GitHub/blob/master/fig/6.png)

比如，我把标题 \title{Workload Trend Analysis} 改为 \title{Workload Analysis}


![1](https://img-blog.csdnimg.cn/20190330215506138.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190330215546556.png)


然后选择push到github上，此时，去github中看,我们发现文件更新了


![如图](https://img-blog.csdnimg.cn/20190330215839662.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwMjAyODk0,size_16,color_FFFFFF,t_70)

说明Overleaf上的文件可以同步到github上了。

## GitHub同步到本地
这个就是git基本操作：
>git pull

git pull一下就行了

## 本地同步到GitHub
>git push
## github同步到Overleaf
当github上项目更新时，Overleaf中会检测到，pull from github也会变成蓝色，此时，点 **Pull GitHub changes into Overleaf** , Overleaf就会自动把GitHub中的更新同步到当前项目中了。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190330230240476.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwMjAyODk0,size_16,color_FFFFFF,t_70)


