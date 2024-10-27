### `ubuntu`设置`sudo`权限→避免每次`sudo`输入密码
    sudo visudo
    
在文件底部添加以下代码，XXX是ubuntu登录用户名  
    XXX  ALL=(ALL) NOPASSWD: ALL
`crtl+X`保存，实现每次`sudo`不需要另外输入密码
