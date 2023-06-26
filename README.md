# trial-gitea

## docker 镜像源配置

### 下载配置文件

```bash
mkdir -p /etc/docker

curl -o /etc/docker/daemon.json https://disk.liuyajie.com/softwares/daemon.json

systemctl restart docker.service
```

### 手动创建

```bash
mkdir -p /etc/docker

touch /etc/docker/daemon.json

echo "
{
  "registry-mirrors": [
    "https://dockerproxy.com",
    "https://hub-mirror.c.163.com",
    "https://mirror.baidubce.com",
    "https://ccr.ccs.tencentyun.com"
  ]
}
" | sudo tee -a /etc/docker/daemon.json

systemctl restart docker.service
```

### 确认配置

```bash
docker info
```

_Registry Mirrors_ 部分应当有相应内容。

## 拉取 Gitea 镜像

```bash
docker pull gitea/gitea:latest
```
