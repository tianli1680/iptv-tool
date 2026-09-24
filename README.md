# iptv-tool (Docker 镜像)

本仓库把本地 `docker save` 导出的镜像 `iptv-tool.tar` 自动发布到
**GitHub 容器仓库 (ghcr.io)**，使其可通过公共 Docker 仓库下载。

## 镜像内容
- 来源 tar：`iptv-tool.tar`（约 32 MB，OCI 布局，`docker save` 导出）
- 原镜像名/标签：`iptv-tool:latest`

## 自动发布流程（GitHub Actions）
推送 `iptv-tool.tar` 或工作流文件到 `main` 分支即触发：
1. `docker load -i iptv-tool.tar` 还原镜像
2. 登录 `ghcr.io`（使用 `GITHUB_TOKEN`）
3. 重新打标签为 `ghcr.io/<owner>/iptv-tool:latest` 并推送
4. 将包设为公开（所有人可 `docker pull`）

## 下载方式
```bash
docker pull ghcr.io/tianli1680/iptv-tool:latest
```

## 本地手动发布（若你本机有 Docker）
```bash
docker load -i iptv-tool.tar
docker tag iptv-tool:latest ghcr.io/tianli1680/iptv-tool:latest
docker login ghcr.io          # 用 GitHub 用户名 + 有 write:packages 权限的令牌
docker push ghcr.io/tianli1680/iptv-tool:latest
```
