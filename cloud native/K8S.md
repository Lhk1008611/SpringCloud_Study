# Kubernetes（K8S）

## 什么是 Kubernetes

- 容器编排系统
- 特性
  - 服务发现和负载均衡
  - 存储编排
  - 自动部署和回滚
  - 自动完成装箱计算
  - 自我修复
  - 秘钥与配置管理

## 架构

### 1. 工作方式

- kubernetes Cluster = N Master Node + N Worker Node
  - K8S 集群由 n 个主节点和 n 个工作节点在组成（n > 1）
  - 有多个（一般是奇数个） master 节点时，遵循多数票原则（少数服从多数原则）选取领导 master 节点

### 2. 组件架构

![](.\image\屏幕截图 2023-10-22 130534.png)

- 各组件解释：
  - [Kubernetes 组件 | Kubernetes](https://kubernetes.io/zh-cn/docs/concepts/overview/components/)

## kubernetes实战

### 搭建 kubernetes 集群

1. 多台服务器

2. 安装 docker

   1. 安装 kubelet

   2. 安装 kubectl

      - 相关命令

        ```shell
        #查看集群所有节点
        kubectl get nodes 
        
        #根据配置文件给集群创建资源（例如创建网络插件）
        kubectl apply -f xxxx.xml
        
        #查看集群部署了哪些应用
        kubectl get pos -A  #等价于 docker ps ，pos 等价于 docker 中的容器
        ```

   3. 安装 kubeadm

      - 使用 docker 分别给 master 节点和 worker 节点安装需要的镜像

      - 搭建集群相关命令
        - `kubeadm init`：初始化 master 节点
        - `kubeadm join`：子节点加入集群

### K8S 自我修复功能

- 应用宕机了会自动重启

### 解决子节点加入集群令牌过期

- 使用命令重新生成加入集群令牌

  ```bash
  kubeadm token create --print-join-command
  ```

### 部署 k8s 可视化界面（dashboard）