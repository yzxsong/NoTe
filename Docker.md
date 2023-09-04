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
## Docker容器
## Docker网络
## Docker存储
## 多主机管理
## 容器网络
## 容器监控
## 日志管理
## 数据管理
## 参考资料
* 《每天5分钟玩转Docker容器技术》
