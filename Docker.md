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
### 容器支持技术
