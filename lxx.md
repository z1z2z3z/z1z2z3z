##### 零星的

```js
//一个字节=8位
/* shift+alt+a 块注释*/
/* shift+up 向上选*/
/* rm -rf 文件名  删除*/
/* CTRL + l */
/* home  该行开头    end  该行末尾    加ctrl  整段的开头或末尾 */
/*正则表达式  ^除了
 *ab+b   +代表前面的字符(b,一个string)必须出现至少一次
 *ab*b   *代表前面的字符(0次,1次,多次)
 *ab?b   ?代表前面的字符最多只可以出现一次(0次,1次)
 */
/* fetch 用post方法  absolute url  == http:// */

/* tail -20 文件名 */ //看文件最后20行   df -h    //du -ah --max-depth=1 /
/* 查看cpu 使用率  top -bn 1 -i -c
    %us：表示用户空间程序的cpu使用率（没有通过nice调度）

    %sy：表示系统空间的cpu使用率，主要是内核程序。

    %ni：表示用户空间且通过nice调度过的程序的cpu使用率。

    %id：空闲cpu

    %wa：cpu运行时在等待io的时间

    %hi：cpu处理硬中断的数量

    %si：cpu处理软中断的数量

    %st：被虚拟机偷走的cpu 
*/
/* 查看几核  cat /proc/cpuinfo |grep "core"|uniq */
/* 查看主频  cat /proc/cpuinfo |grep MHz|uniq */
/* 查看cpu个数 cat /proc/cpuinfo |grep "physical id"|sort |uniq|wc -l */
/* python里的add_experimental_option(前,后)改成options.前(后) */

//默认打开某一文件,改package.json部分  ("main": "index.js")

/** 
 *  1.Node是什么？
    Node是一个基于ChromeV8引擎的JavaScript代码运行环境。
    简单理解：像浏览器可以运行JavaScript代码一样，它是一个可以运行JavaScript代码的软件。
*   2.Node.js的组成
    Node.js是由ECMAScript+Node模块API组成。
*   3.Node.js基础语法
    所有ECMAScript语法在Node环境中都可以使用。 */

/** 
 * ssh + ip地址
 * 虚拟机  查看网络配置:vim /etc/sysconfig/network-scripts/ifcfg-rth0
 * ping + 网址：测试网络
 * 屏幕翻页快捷键
 
shift+PgUp      向前翻看,一般翻13页左右。
shift+PgDown   向后翻看,一般翻13页左右。
 
先通过 git branch -a 获取所有的分支
然后通过  git log + 上面获取的分支名(要查看日志的分支)


 
我们翻阅目录和打开文件后，经常会由于输出内容太多，使一屏无法显示，所以我们要经常用到这些命令,下面我们尝试下这些命令：
 
ls -l /etc |more
less -N /etc/profile 显示行号
less的动作命令:
j 向下移动一行；同vi
k 向上移动一行；同vi
f 向下滚动一屏；forword
b 向上滚动一屏；backword
head -n 10 /etc/profile   显示/etc/profile的前10行内容
tail -n 5 /etc/profile    显示/etc/profile的最后5行内容
 
以上部分命令，请使用q退出。
 
 
下面我们就细说下这几个命令
 
more
 
more 是我们最常用的工具之一，最常用的就是显示输出的内容，然后根据窗口的大小进行分页显示，然后还能提示文件的百分比；
 
# more /etc/profile
 
more 的语法、参数和命令；
more [参数选项] [文件]
 
参数如下：
+num                              从第num行开始显示；
-num                              定义屏幕大小，为num行；
+/pattern                      从pattern 前两行开始显示；
-c                                 从顶部清屏然后显示；
-d                                 提示Press space to continue, 'q' to quit.（按空 键继续，按q键退出），禁用响铃功能；
-l                                 忽略Ctrl+l （换页）字符；
-p                                 通过清除窗口而不是滚屏来对文件进行换页。和-c参数有点相似； 
-s                                 把连续的多个空行显示为一行；
-u                                 把文件内容中的下划线去掉
 
退出more的动作指令是q
 
more 的参数应用举例；
# more -dc /etc/profile      注：显示提示，并从终端或控制台顶部显示；
# more +4 /etc/profile         注：从profile的第4行开始显示；
# more -4 /etc/profile         注：每屏显示4行；
# more +/MAIL /etc/profile       注：从profile中的第一个MAIL单词的前两行开始显示；
 
more 的动作指令；
 
我们查看一个内容较大的文件时，要用到more的动作指令，比如ctrl+f（或空格键）是向下显示一屏，ctrl+b是返回上一屏； Enter键可以向下滚动显示n行，要通过定，默认为1行；
 
以下几个常用的；
Enter             向下n行，需要定义，默认为1行；
Ctrl+f            向下滚动一屏；
空 键             向下滚动一屏；
Ctrl+b            返回上一屏；
=                   输出当前行的行号；
:f                  输出文件名和当前行的行号；
v                   调用vi编辑器；
! 命令            调用Shell，并执行命令；
q                   退出more
 
当我们查看某一文件时，想调用vi来编辑它，不要忘记了v动作指令，这是比较方便的；
 
其它命令通过管道和more结合的运用例子；
比如我们列一个目录下的文件，由于内容太多，我们应该学会用more来分页显示。这得和管道 | 结合起来，比如：
# ls -l /etc   |more
 
 
less 
 
less 查看文件内容 工具；
less 工具也是对文件或其它输出进行分页显示的工具，应该说是linux正统查看文件内容的工具，功能极其强大；您是初学者，我建议您用less。由于less的内容太多，我们把最常用的介绍一下；
 
less的语法格式；
less [参数]   文件 
 
常用参数
-c 从顶部（从上到下）刷新屏幕，并显示文件内容。而不是通过底部滚动完成刷新；
-f 强制打开文件，二进制文件显示时，不提示警告；
-i 搜索时忽略大小写；除非搜索串中包含大写字母；
-I 搜索时忽略大小写，除非搜索串中包含小写字母；
-m 显示读取文件的百分比；
-M 显法读取文件的百分比、行号及总行数；
-N 在每行前输出行号；
-p   pattern 搜索pattern；比如在/etc/profile搜索单词MAIL，就用 less -p MAIL /etc/profile
-s 把连续多个空白行作为一个空白行显示；
-Q 在终端下不响铃；
 
比如：我们在显示/etc/profile的内容时，让其显示行号；
# less -N      /etc/profile
 
less的动作命令；
进入less后，我们得学几个动作，这样更方便我们查阅文件内容；最应该记住的命令就是q，这个能让less终止查看文件退出；
 
动作
回车键 向下移动一行；
y 向上移动一行；
空格键 向下滚动一屏；
b 向上滚动一屏；
d 向下滚动半屏；
h less的帮助；
u 向上洋动半屏；
w 可以指定显示哪行开始显示，是从指定数字的下一行显示；比如指定的是6，那就从第7行显示；
g 跳到第一行；
G 跳到最后一行；
p n% 跳到n%，比如 10%，也就是说比整个文件内容的10%处开始显示；
/pattern 搜索pattern ，比如 /MAIL表示在文件中搜索MAIL单词；
v 调用vi编辑器；
q 退出less
!command 调用SHELL，可以运行命令；比如!ls 显示当前列当前目录下的所有文件；
 
就less的动作来说，内容太多了，用的时候查一查man less是最好的。在这里就不举例子了；
 
head
 
head 是显示一个文件的内容的前多少行；
 
用法比较简单；
head   -n   行数值   文件名；
 
比如我们显示/etc/profile的前10行内容，应该是：
# head -n 10 /etc/profile
 
tail
 
tail 是显示一个文件的内容的后多少行；
用法比较简单；
tail    -n   行数值   文件名；
 
比如我们显示/etc/profile的最后5行内容，应该是：
# tail   -n 5 /etc/profile
    
*/
///真正进行通信的实体是在主机的进程
/**   tcp(传送数据前先建立链接,数据传输完成后要释放链接)  端对端的通信(应用进程之间的通信)   ip网络层可实现两个主机间的通信
 * TCP，提供面向连接的服务，在传送数据之前必须先建立连接，数据传送完成后要释放连接。因此TCP是一种可靠的的运输服务，但是正因为这样，不可避免的增加了许多的开销，比如确认，流量控制等。对应的应用层的协议主要有 SMTP,TELNET,HTTP,FTP 等。 
 * TCP把连接作为最基本的对象，每一条TCP连接都有两个端点，这种断点我们叫作套接字（socket），它的定义为端口号拼接到IP地址即构成了套接字，例如，若IP地址为192.3.4.16 而端口号为80，那么得到的套接字为192.3.4.16:80。
 * 
 */




/** 
 * JQ 选择元素时,原属性含有空格移到$里,改成'.',  class  ===>  '.class'   id  ====> '#id'
 * 在网页控制台引入jQ方法:
 * http:    ;(function(d,s){d.body.appendChild(s=d.createElement('script')).src='http://cdn.bootcss.com/jquery/1.11.0/jquery.min.js'})(document);
 * https:   ;(function(d,s){d.body.appendChild(s=d.createElement('script')).src='https://cdn.bootcss.com/jquery/1.11.0/jquery.min.js'})(document); 
 * 某些特征网站:  ;(function(d,s){d.body.appendChild(s=d.createElement('script')).src='https://libs.baidu.com/jquery/2.0.0/jquery.min.js'})(document);
 */

/** 
 * git add + file
 * git commit -m '注释'
 * git push
 */  


/* 
cmd 命令 node  前面加'.'  例如(.exit)
*/

//压缩相关的

/*
　　解包：tar zxvf FileName.tar

　　打包：tar czvf FileName.tar DirName
　　
　　去掉某个文件打包：tar czvf FileName(打包到文件) --exclude=/home/node_modul(注意前后都不要有斜杠) DirName(被打包文件)
(可以并列去掉多个)

gz命令

　　解压1：gunzip FileName.gz

　　解压2：gzip -d FileName.gz

　　压缩：gzip FileName

　　.tar.gz 和 .tgz

　　解压：tar zxvf FileName.tar.gz

　　压缩：tar zcvf FileName.tar.gz DirName

   压缩多个文件：tar zcvf FileName.tar.gz DirName1 DirName2 DirName3 ...

bz2命令

　　解压1：bzip2 -d FileName.bz2

　　解压2：bunzip2 FileName.bz2

　　压缩： bzip2 -z FileName

　　.tar.bz2

　　解压：tar jxvf FileName.tar.bz2

　　压缩：tar jcvf FileName.tar.bz2 DirName

bz命令

　　解压1：bzip2 -d FileName.bz

　　解压2：bunzip2 FileName.bz

　　压缩：未知

　　.tar.bz

　　解压：tar jxvf FileName.tar.bz

Z命令

　　解压：uncompress FileName.Z

　　压缩：compress FileName

　　.tar.Z

　　解压：tar Zxvf FileName.tar.Z

　　压缩：tar Zcvf FileName.tar.Z DirName

zip命令

　　解压：unzip FileName.zip

　　压缩：zip -r FileName.zip DirName
　　
　　读磁盘：df -h
*/


/data/Uniswap_defi
```



```bash
$ mkdir egg-example && cd egg-example
$ npm init egg --type=simple
$ npm i
```

```
删除images docker rmi <image id>  ///未运行 pull下来是镜像
删除container  docker rm -f <container id>  ///在容器里运行
```

