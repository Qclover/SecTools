# SecTools
## 1.fingerSPider（RootPath） 网站指纹批量识别
### 0x1 domains.txt 要识别的网站
### 0x2 从finger.json提取指定指纹的url

## 2.nikto
install

docker search nikto

docker pull kenney/nikto

docker inspect kenney/nikto

docker run --rm -t kenney/nikto:latest nikto -h www.163.com -p 443

这里的–rm指的是执行完清理容器，这样就不会有日志什么的残留在主机上

等待一会可以看到结果输出

使用LibWhisker中对IDS的躲避技术，可使用以下几种类型：

　　1. 随机URL编码(非UTF-8方式)

　　2. 自选择路径(/./)

　　3. 虚假的请求结束

　　4. 长的URL请求

　　5. 参数隐藏

　　6. 使用TAB作为命令的分隔符

　　7. 大小写敏感

　　8. 使用Windows路径分隔符\替换/

　　9. 会话重组

-findonly

　　仅用来发现HTTP和HTTPS端口，而不执行检测规则

-Format

　　指定检测报告输出文件的格式，默认是txt文件格式(csv/txt/htm)

-host

　　目标主机，主机名、IP地址、主机列表文件。

-id

　　ID和密码对于授权的HTTP认证。格式：id:password

-mutate

　　变化猜测技术

　　1.使用所有的root目录测试所有文件

　　2.猜测密码文件名字

　　3.列举Apache的用户名字(/~user)

　　4.列举cgiwrap的用户名字(/cgi-bin/cgiwrap/~user)

-nolookup

　　不执行主机名查找

-output

　　报告输出指定地点

-port

　　扫描端口指定，默认为80端口。

-Pause

　　每次操作之间的延迟时间

-Display

　　控制Nikto输出的显示

　　1.直接显示信息

　　2.显示的cookies信息

　　3.显示所有200/OK的反应

　　4.显示认证请求的URLs

　　5.Debug输出

-ssl

　　强制在端口上使用SSL模式

-Single

　　执行单个对目标服务的请求操作。

-timeout

　　每个请求的超时时间，默认为10秒

-Tuning

　　Tuning 选项控制Nikto使用不同的方式来扫描目标。

　　0.文件上传

　　1.日志文件

　　2.默认的文件

　　3.信息泄漏

　　4.注射(XSS/Script/HTML)

　　5.远程文件检索(Web 目录中)

　　6.拒绝服务

　　7.远程文件检索(服务器)

　　8.代码执行-远程shell

　　9.SQL注入

　　a.认证绕过

　　b.软件关联

　　g.属性(不要依懒banner的信息)

　　x.反向连接选项

-useproxy

　　使用指定代理扫描

-update

　　更新插件和数据库
### 查看结果
将本地目录挂载到容器中，将结果输出到该目录，使得我们能在运行结束后拿到结果

docker run -v /home/root/data/:/root --rm -t kenney/nikto:latest nikto -h c.163.com -p 443 -o /root/result.html -F htm
运行完后查看主机目录

/home/root/data# ls -lrt
total 8
drwxr-xr-x 2 root root 4096 Nov  1 16:06 log
-rw-r--r-- 1 root root 3825 Nov  1 19:04 result.html
