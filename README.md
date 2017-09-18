# 购买服务器
https://www.50vz.net/

购买前记得注册用户

shadowsocks不需要太高的配置，咱们选择最基础的配置就可以啦!

我选择的是洛杉矶C3，最低的默认配置

`20.00RMB/月`

支付宝付款^_^

在购买完服务器后，你会收到一封邮件：

[[file:tutorial/mail.png]]

务必保存好这封邮件，以免之后遗忘。

## 划红线的是咱们要关心的：
主IP: `XXX.XXX.XXX.XXX`
Root 密码： `XXXXXXXXXXXXXXXXXXXXXX`

# 第一次连接服务器

1. 打开Mac Os 的终端(Terminal)

2. 通过ssh 协议远程连接服务器:

	ssh -p portNumber user@host

	Example:

		ssh -p 22 root@107.151.172.246

	107.151.172.246 是我的主IP，请替换成自己的;

	ssh 默认使用端口号 22

3. 远程服务器相应，是否继续连接？

	Are you sure you want to continue connecting (yes/no)?
				
		yes

4. 远程服务器询问Root密码:

	root@xxx.xxx.xxx.xxx's password:

	`直接复制，以免打错(总之别打错！！！)`

	`提一下，输入密码的时候，命令行光标和屏幕是不显示的，不要觉得奇怪`

5.  成功登陆! 

				_____________________________   _________   _________________
    			_  __ \__  __ \  _ \_  __ \_ | / /__  /_ | / /__  __ \_  ___/
    			/ /_/ /_  /_/ /  __/  / / /_ |/ /__  /__ |/ /__  /_/ /(__  ) 
    			\____/_  .___/\___//_/ /_/_____/ _____/____/ _  .___//____/  
          		/_/                                    /_/            
				Welcome to openvzvps.cc Virtual Private Server service 


6. 首次登陆时，远程可能会提示 修改ssh默认端口号; `如果你修改了端口号，一定要记下来！`

		Example: 22 -> 2345 
	
7. 熟悉一下远程环境，结束第一次远程服务器访问:

	exit


# 建立shadowsocks 服务器
1.	ssh 远程连接服务器， 记住如果修改了 ssh 默认端口号，请用新的端口号登录
	Example:

		ssh -p 2345 root@xxx.xxx.xxx.xxx
2.	安装Shadowsocks 服务器:

		yum update
		yum install python-setuptools && easy_install pip
		pip install shadowsocks


3.	配置一个基本的Shadowsocks 服务器:

	这里我们需要用到vi 编辑器 (不要慌。。。)
			
		vi /etc/shadowsocks.json
			
	按 ‘i’  进入编辑模式，

	按如下格式输入如下内容：


		{
		"server":"XXX.XXX.XXX.XXX",
		"local_address":"127.0.0.1",
		"local_port":1080,
		"port_password":{
			"443":"your password"
		},
		"timeout":300,
		"method":"aes-256-cfb",
		"fast_open":false
		}

	其中 Server 就是你的 主IP; 

	Your Password 是shadowsocks登陆密码;
			
	按 'Esc' 退出编辑模式

	键入 ':wq' 保存退出

		Esc
		:wq
	
4.	进行到这里，已经完成90%的工作了，在终端输入下面的命令
				
		echo “/usr/bin/ssserver -c /etc/shadowsocks.json -d start” >> /etc/rc.local
			
5. 	重启远程服务器

		reboot

6.	Okay!!! 服务器搭建完成
	
		^_^
	
7.	尝试登陆一下自己的服务器吧！

	服务器地址：xxx.xxx.xxx.xxx

	端口：443

	your password：登录密码


		
			
			
			
			
			
			
			
			
			
			
			
			
			
			
	
	
	
	
	
		
