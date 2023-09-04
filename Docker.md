# Docker
## 目录
## 容器生态系统
### 容器核心技术
* 容器规范：保证不同容器间的兼容，OCI制定开放的容器规范。runtime spec和image format spec
* 容器runtime：容器真正运行的地方，与操作系统内核紧密协作，为容器提供运行环境。主流runtime：lxc、runc、rkt
* 容器管理工具：对内与runtime交互、对外为用户提供interface。lxc-lxc、runc-docker engine（deamon、cli）、rkt-rkt cli
* 容器定义工具：允许用户定义容器的内容和属性，从而让容器能被保存、共享和重建。docker image、dockerfile、ACI
* Registries：存放image。Docker Registries、Docker Hub、 Quay.io
* 容器OS:专门运行容器的操作系统。Coreos、atomic、ubuntu core
### 容器平台技术
* 容器编排引擎：通常包括容器管理、调度、集群定义和服务发现等。docker swarm、kubernetes、mesos
* 容器管理平台：架构在编排引擎之上、支持多种编排引擎。Rancher、ContainerShip
* 基于容器的PaaS：提供开发、部署和管理应用的平台，使用户不必关心底层基础设施。Deis、Flynn、Dokku
### 容器支持技术
* 容器网络：容器使网络拓扑变的动态和复杂，需要专门的解决方案来管理容器与容器、容器与其他实体之间的连通性和隔离性。docker network、flannel、weave、calico
* 服务发现：保存容器中所有微服务最新消息，比如IP和端口，并对外提供API、提供服务查询功能。etcd、consul、zookeeper
* 监控：docker ps/top/stats、docker stats API、sysdig、cAdvisor/Heapster、Weave Scope
* 数据管理：保持持久化数据也能够动态迁移。Rex-Ray
* 日志管理:docker logs、logspout
* 安全性：openSCAP
## Docker架构
* Docker客户端：Client
* Docker服务器： Docker daemon
* Docker 镜像： Image
* Registry
* Docker容器： Container

![Docker架构](https://github.com/yzxsong/NoTe/blob/main/images/Docker/Docker%E6%9E%B6%E6%9E%84.png)
## Docker镜像
### 镜像的内部结构
#### Base镜像
* 不依赖其他镜像，从scratch构建
* 其他镜像可以以此为基础进行扩展
#### 镜像的分层结构
* 优点：共享资源
* 可写的容器层：所有对容器的改动都只会发生在容器层中

![镜像的分层结构](https://github.com/yzxsong/NoTe/blob/main/images/Docker/%E9%95%9C%E5%83%8F%E7%9A%84%E5%88%86%E5%B1%82%E7%BB%93%E6%9E%84.png)
### 构建镜像
#### docker commit
* 运行容器
* 修改容器
* 将容器保存为新的镜像
#### Dockerfile
* 从base镜像运行一个容器
* 执行一条指令，对容器做修改
* 执行类似docker commit的操作，生成一个新的镜像层
* Docker再基于刚刚提交的镜像运行一个新容器
* 重复上面操作
##### 常用指令
* FROM：指定base镜像
* MAINTAINER：设置镜像的作者
* COPY：将文件从build context复制到镜像
* ADD：类似COPY、会自动解压
* ENV：设置环境变量
* EXPOSE：指定容器中的进行监听某个端口
* VOLUME：将文件或目录声明为volume
* WORKDIR：设置当前工作目录
* RUN：在容器中运行指定的命令。执行命令并创建新的镜像层，经常用于安装软件包
* CMD：容器启动时运行指定的命令。会被docker run 命令行后面的参数替换
* ENTRYPOINT：设置容器启动时运行的命令，不会被忽略。可用CMD提供额外的参数
### 分发镜像
* 利用Dockerfile创建
* 将镜像上传到Registry
* 搭建私有Registry
## Docker容器
### 运行容器
* docker run： -d后台常驻、-it 交互式终端
### 进入容器
* attach：直接进入，不启用新进程
* exec：打开新的终端，启动新进程
### 资源限制
#### 内存限额
* -m/--memory： 设置内存限额
* --memory-swap：设置内存swap的使用限额
#### CPU限额
* -c/--cpu-shares
### 实现容器的底层技术
#### cgroup
Linux设置进程使用CPU、内存和IO资源的限额
#### namespace
管理host中全局唯一的资源，让每个容器都觉得只有自己在使用它。
* Mount namespace：让容器看上去拥有整个文件系统
* UTS namespace：让容器拥有自己的hostname
* IPC namespace：让容器拥有自己的共享内存和信号量来实现进程间通信
* PID namespace：让容器拥有一套独立的PID
* Network namespace: 让容器拥有自己独立的网卡、IP、路由等资源
* User namespace：让容器管理自己的用户
## Docker网络
## Docker存储
## 多主机管理
## 容器网络
## 容器监控
## 日志管理
## 数据管理
## 参考资料
* 《每天5分钟玩转Docker容器技术》
