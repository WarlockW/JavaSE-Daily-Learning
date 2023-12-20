<h1>Linux环境</h1>
<h2>JDK安装</h2>
linux环境安装JDK直接下载对应系统架构的软件包放到对应的路径下即可（以将JDK放置在 /opt/module/ 路径下为例) 

![image](https://github.com/WarlockW/JavaSE_Daily_Learning/blob/main/JavaSE%20Notebook/Session_0%20JAVA%E5%9F%BA%E7%A1%80%E5%86%85%E5%AE%B9/Static/0-0.png)

<h2>配置环境变量</h2>
linux环境下，配置环境变量在 /etc/profile.d 中新建一个.sh脚本，将相关的配置项配置在文件中。（linux系统在启动后会自动运行 /etc/profile ，该脚本其中有一部分代码是运行全部 /etc/profile.d 路径下的所有.sh脚本，因此可以在profile.d中自定义脚本文件，并将环境变量配置进去）

本例中在 /etc/profile.d/ 路径下建立 MY_ENV.sh 脚本，并将环境变量配置在文件中。

![image](https://github.com/WarlockW/JavaSE_Daily_Learning/blob/main/JavaSE%20Notebook/Session_0%20JAVA%E5%9F%BA%E7%A1%80%E5%86%85%E5%AE%B9/Static/0-1.png)

![image](https://github.com/WarlockW/JavaSE_Daily_Learning/blob/main/JavaSE%20Notebook/Session_0%20JAVA%E5%9F%BA%E7%A1%80%E5%86%85%E5%AE%B9/Static/0-2.png)
