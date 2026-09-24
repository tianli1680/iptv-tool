# iptv-tool (Docker 镜像)

## 下载方式
```bash
docker pull ghcr.io/tianli1680/iptv-tool:latest
```

## 运行方式
```bash
docker run -d --name tv-tool -v /etc/epg:/htdocs/data -p 5678:80 --restart unless-stopped ghcr.io/tianli1680/iptv-tool:latest
```
