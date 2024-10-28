[docker修改镜像源](#docker修改镜像源)  
[docker拉取镜像,查看镜像](#docker拉取镜像)  
[启动docker容器](#启动docker容器)  
[jupyter调试docker容器  ](#jupyter调试docker容器)  
[docker查看正在运行的容器](#docker查看正在运行的容器)  

# `docker`修改镜像源
需要已安装`vim`

    (sudo) vi /etc/docker/daemon.json  

在文本中`registry-mirrors`部分添加镜像源  
附`vim`命令    

- 进入文本`insert`模式：键入`i`  
- 结束文本插入：键入`Esc`  
- 保存文件：键入`:`，然后键入`w+q`  

# `docker`拉取镜像
查看镜像  

    (sudo) docker image ls  

拉取镜像

    (sudo) docker pull (镜像名)

# 启动`docker`容器

    (sudo) docker run -it -p 8891:8891 --rm -v (in_path):(out_path) tigrlab/fmriprep_ciftify:v1.3.2-2.3.3  

附加启动指令  
- `-d`后台模式运行容器  
- `--rm`退出容器的时候自动移除容器，不需要手动删除  
- `-it`进入容器的交互模式  
- `--name [name]`为容器命名  
- `-v`本地文件夹只可读，`rw`读写  
- `-p xxxx:yyyy`指定容器的端口  

# `jupyter`调试`docker`容器  
先要启动一个容器并指定端口
### 生成`jupyter notebook`配置文件

    apt-get install jupyter
    apt-get install ipython  或者  sudo apt install python3-ipython
    jupyter notebook --generate-config

### 生成密码、修改配置文件  
    jupyter notebook password  
    (sudo) vi /root/.jupyter/jupyter_notebook_config.json   

在`json`文件中将生成密文，复制该密文  

    (sudo) vi /root/.jupyter/jupyter_notebook_config.py  

进入`insert`模式，添加或者修改这几行

    c.NotebookApp.ip='*'  
    c.NotebookApp.password = u'刚才复制的那个密文'  
    c.NotebookApp.open_browser = False  
    c.NotebookApp.port =8891   

### 安装`python3-dev`  

    (sudo) apt-get install python3-dev

### 安装`ipykernel`  

    pip install ipykernel
    python -m ipykernel install --user --name (环境名称)

### 启动`jupyter`

    jupyter notebook --ip=0.0.0.0 --no-browser --allow-root --port 8891

### 本地`ssh`连接

    ssh -L 8891:localhost:8891 [用户名]@[主机IP]

浏览器打开`http://localhost:8891`，输入登录密码即可

# `docker`查看正在运行的容器

    (sudo) docker ps -a 
