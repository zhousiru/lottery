# Lottery

基于 WebSocket 的在线发号 & 摇号抽奖 Web App

## Preview

[lott.mofu.app](https://lott.mofu.app)（此部署限制单 Lobby 最多 2000 人在线）

<p align="center">
  <img src="docs/home.webp" width="75%">
  <img src="docs/screen.webp" width="75%">
</p>

## Deploy

```sh
docker compose pull
docker compose up -d
```

然后访问 `http://localhost:3080`

需要 Docker Compose v2.24.0 或更高版本。前端和后端镜像由 GitHub Actions 构建并发布到 GHCR，部署时无需源码构建（支持 `linux/amd64`）。

`main` 分支发布 `latest`，版本标签（`v*`）发布同名镜像标签，每次构建还会发布 `sha-<完整提交 SHA>`。可在 `.env` 中设置 `LOTTERY_TAG`，让前后端使用同一版本。首次发布后需在 GitHub Packages 中将两个镜像设为 Public，或先登录 GHCR。

也可以创建 `compose.override.yaml` 来重写 Docker Compose 配置。

## Configure

参考 `.env.backend.example` 创建 `.env.backend`，Compose 会自动加载；也可以在 `compose.override.yaml` 中设置环境变量。未设置时使用应用默认值。

抽奖房间保存在内存中，重启后端会清空房间。

## Development

```sh
pnpm i
pnpm dev:backend
pnpm dev:web
```
