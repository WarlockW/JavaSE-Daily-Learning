<h1>Linux环境</h1>
<h2>JDK安装</h2>
linux环境安装JDK直接下载对应系统架构的软件包放到对应的路径下即可（以将JDK放置在 /opt/module/ 路径下为例) 
<br/><br/>

![image](https://github.com/WarlockW/JavaSE_Daily_Learning/blob/main/JavaSE%20Notebook/Session_0%20JAVA%E5%9F%BA%E7%A1%80%E5%86%85%E5%AE%B9/Static/0-0.png)

<h2>配置环境变量</h2>
linux环境下，配置环境变量在 /etc/profile.d 中新建一个.sh脚本，将相关的配置项配置在文件中。（linux系统在启动后会自动运行 /etc/profile ，该脚本其中有一部分代码是运行全部 /etc/profile.d 路径下的所有.sh脚本，因此可以在profile.d中自定义脚本文件，并将环境变量配置进去）
<br/><br/>
本例中在 /etc/profile.d/ 路径下建立 MY_ENV.sh 脚本，并将环境变量配置在文件中。
<br/><br/>

![image](https://github.com/WarlockW/JavaSE_Daily_Learning/blob/main/JavaSE%20Notebook/Session_0%20JAVA%E5%9F%BA%E7%A1%80%E5%86%85%E5%AE%B9/Static/0-1.png)

在 MY_ENV.sh 文件中写入配置
<br/><br/>
![image](https://github.com/WarlockW/JavaSE_Daily_Learning/blob/main/JavaSE%20Notebook/Session_0%20JAVA%E5%9F%BA%E7%A1%80%E5%86%85%E5%AE%B9/Static/0-2.png)
<br/><br/>
注意事项：<br>
1.export可以理解为从内存中获取变量，并用“=”赋值<br>
2.linux环境变量PATH使用“:”进行分隔<br>
3.添加环境变量完成后，使用命令 source /etc/profile 重新加载配置文件，使得刚才配置好的环境变量生效<br>
```
# JAVA环境变量配置
# 把“JAVA_HOME”变量从内存中导出，并以JDK的路径进行赋值
export JAVA_HOME=/opt/module/jdk-15.0.2

# 把“PATH”变量从内存中导出，并以$JAVA_HOME/bin进行赋值（linux以“:”符号作为PATH环境变量的分隔符号）
export PATH=$PATH:$JAVA_HOME/bin
```
