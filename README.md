# Desc

本仓库仅用于个人网络实验，通过 [containerlab](https://containerlab.dev/quickstart/) 模拟网络拓扑

# Usage

首先，通过官方脚本安装 `containerlab`

```shell
curl -sL https://containerlab.dev/setup | sudo -E bash -s "all"
```

然后克隆本仓库，并通过 `deploy` 命令部署拓扑

```shell
git clone https://github.com/baimowen/xxx.git $HOME/topology && cd $_
sudo containerlab deploy -t topology.clab.yaml
```

## question

此拓扑使用 arista/ceos:4.32.0F 镜像。必须首先注册并登录然后从此处下载镜像[Arista](https://www.arista.com/zh/support/software-download)并将其导入到 Docker 中。

```shell
scp cEOS-lab-4.32.0F.tar.xz server_name@username:$HOME
xz -dc cEOS-lab-4.32.0F.tar.xz | docker import - arista/ceos:4.32.0F
```

## graph

通过 `graph` 命令快速生成web服务，便于查看拓扑结构

```shell
sudo containerlab graph -t topology.clab.yaml
```

>  如果外部网络或宿主机访问，需确保防火墙放行50080端口
