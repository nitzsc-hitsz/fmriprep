[ubuntu设置sudo权限](#ubuntu设置sudo权限) 
[docker修改镜像源](#docker修改镜像源) 
[docker拉取镜像,查看镜像](#docker拉取镜像) 
[启动docker容器](#启动docker容器) 



# `ubuntu`设置`sudo`权限
    sudo visudo
    
在文件底部添加以下代码，`XXX`是`ubuntu`登录用户名  
    
    XXX ALL=(ALL) NOPASSWD: ALL 
`crtl+X`保存，实现每次`sudo`不需要另外输入密码

# `docker`修改镜像源
需要已安装`vim`

    (sudo) vi /etc/docker/daemon.json  

在文本中`registry-mirrors`部分添加镜像源  
附`vim`命令    

进入文本插入模式：键入`i`  
结束文本插入：键入`Esc`  
保存文件：键入`:`，然后键入`w+q`  

# `docker`拉取镜像
查看镜像  

    (sudo) docker image ls  

拉取镜像

    (sudo) docker pull (镜像名)

# 启动`docker`容器

    sudo docker run -it -p 9999:9999 --rm -v (in_path):(out_path) tigrlab/fmriprep_ciftify:v1.3.2-2.3.3
