# trial-gitea

[官方网站](https://docs.gitea.com/)

## 【可选】docker 镜像源配置

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

## 启动服务

```bash
docker compose up -d
```

# 初始化

GUI [http://localhost:3000](http://localhost:3000)

## 注册管理员账户

[注册第一个用户](http://localhost:3000/user/sign_up)，该用户将自动成为管理员。

## 常用操作

- [迁入代码库](http://localhost:3000/repo/migrate)
