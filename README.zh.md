# Tinyproxy - 轻量级代理服务器（Docker 化，支持 ACL 配置）

> 一个快速且易于使用的 Docker 化 Tinyproxy 镜像，支持可配置的访问控制列表（ACL）。

## 项目简介

Tinyproxy 是一个轻量级 HTTP/HTTPS 代理服务器。该项目将 Tinyproxy 容器化，用户可以通过修改配置轻松设置访问控制列表，实现对代理访问的灵活管理。

- 基于 Shell 脚本自动化配置
- 简单快捷的 Docker 部署方式
- 支持自定义 ACL，灵活管理访问权限

## 快速开始

### 1. 拉取镜像

```bash
docker pull <你的镜像地址，例如 doitky/tinyproxy>
```

### 2. 运行容器

```bash
docker run -d \
  --name tinyproxy \
  -p 8888:8888 \
  -v $(pwd)/tinyproxy.conf:/etc/tinyproxy/tinyproxy.conf \
  doitky/tinyproxy
```

### 3. 配置 ACL

编辑 `tinyproxy.conf` 文件，根据需求添加或修改 ACL 规则：

```
# 允许的 IP
Allow 192.168.0.0/16
Allow 10.0.0.0/8
# 拒绝其他所有
Deny 0.0.0.0/0
```

## 配置参数说明

- 端口映射可通过 `-p` 参数设置（默认 8888）
- 通过挂载配置文件 `-v` 实现自定义 Tinyproxy 行为
- 支持标准 Tinyproxy 配置项

## License

MIT

## 参考文档

- [Tinyproxy 官方文档](https://tinyproxy.github.io/)
- [Docker 官方文档](https://docs.docker.com/)

---

如果你觉得本项目对你有帮助，欢迎 Star！