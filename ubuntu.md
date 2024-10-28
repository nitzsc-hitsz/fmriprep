[ubuntu设置sudo权限](#ubuntu设置sudo权限)    
[Ubuntu文件夹命令](#Ubuntu文件夹命令)  
[推荐使用jupyter复制移动文件](#推荐使用jupyter复制移动文件)

# `ubuntu`设置`sudo`权限
    sudo visudo
    
在文件底部添加以下代码，`XXX`是`ubuntu`登录用户名  
    
    XXX ALL=(ALL) NOPASSWD: ALL 
`crtl+X`保存，实现每次`sudo`不需要另外输入密码


# `Ubuntu`文件夹命令
创建文件夹

    (sudo) mkdir /xx/xx

修改文件夹权限,`777`指所有人都可读取和写入

    (sudo) chmod 777 /文件夹目录

# 推荐使用`jupyter`复制移动文件
先打开`jupyter notebook`  

    import shutil  
    shutil.copy(/path1/filename,/path2)  
