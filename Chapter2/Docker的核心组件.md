- **Docker客户端：Client**

  docker命令，也可通过REST API与服务器通信

- **Docker服务端：Docker daemon**

  服务器组件，运行在Host上，负责创建、运行、监控容器，构建、存储镜像

  默认只响应本地客户端请求，如果需要允许远程客户端请求，需要打开TCP监听。

  1.路径：/etc/systemd/system/multi-user.target.wants/docker.service

  允许来自任意IP的客户端连接

  ```java
  ExecStart=/usr/bin/dockerd -H tcp://0.0.0.0
  ```

  <font color="red">不同系统配置文件位置可能不同</font>

  2.重启Docker daemon

  ```java
  systemctl daemon-reload
  systemctl restart docker.service
  ```

  3.服务器IP为192.168.1.102，客户端在命令行加上-H参数，即可远程通信

  ```java
  docker -H 192.168.1.102 info
  info命令可以查看Docker服务器信息
  ```

- **Docker镜像：Image**

  只读模板，可以创建容器

  生成方法：从无到有开始创建镜像、下载并使用别人现成的镜像、在现有镜像之上创建新镜像

  <font color="red">可以将镜像内容和创建步骤描述在文本文件中，称为Dockerfile,通过执行docker build <docker-file>命令可以构建Docker镜像</font>

- **Registry**

  存放Docker镜像的仓库，分公有和私有两种

  Docker Hub(https://hub.docker.com/)是默认的Registry

  docker pull：下载镜像

  docker run：先下载镜像（本地没有），再启动容器

  docker ps或docker container ls显示容器正在运行

- **Docker容器：Container**