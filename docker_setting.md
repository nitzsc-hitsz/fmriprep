### ubuntu设置sudo权限→避免每次sudo输入密码
    sudo visudo
在文件底部添加以下代码  
    (XXX) ALL=(ALL) NOPASSWD: ALL  
crtl+X保存，实现每次sudo不需要另外输入密码
