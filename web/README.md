# 🦌 DeerFlow Web 界面

[![许可证：MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> 源于开源，回馈开源。

这是 [`DeerFlow`](https://github.com/bytedance/deer-flow) 的网页 UI。

## 快速开始

### 前置条件

- [`DeerFlow`](https://github.com/bytedance/deer-flow)
- Node.js (v22.14.0+)
- pnpm（v10.6.2+）作为包管理器

### 配置

在项目根目录中创建一个 `.env` 文件，并配置以下环境变量：

- `NEXT_PUBLIC_API_URL`：deer-flow API 的 URL。

建议始终从提供的示例文件开始，并使用你自己的值编辑 `.env` 文件：

```bash
cp .env.example .env
```

## 如何安装

DeerFlow Web UI 使用 `pnpm` 作为包管理器。要安装依赖项，请运行：

```bash
cd web
pnpm install
```

## 如何以开发模式运行

> [!NOTE]
> 启动 Web UI 前，请确保 Python API 服务正在运行。

启动 Web UI 开发服务器：

```bash
cd web
pnpm dev
```

默认情况下，可通过 `http://localhost:3000` 访问 Web UI。

如果你使用其他主机或位置，可以设置 `NEXT_PUBLIC_API_URL` 环境变量。

```ini
# .env
NEXT_PUBLIC_API_URL=http://localhost:8000/api
```

## Docker

你也可以使用 Docker 运行此项目。

首先，你需要阅读下面的[配置](#配置)。确保 `.env` 文件已准备就绪。

其次，构建你自己的 Web 服务器 Docker 镜像：

```bash
docker build --build-arg NEXT_PUBLIC_API_URL=YOUR_DEER-FLOW_API -t deer-flow-web .
```

最后，启动运行 Web 服务器的 Docker 容器：

```bash
# Replace deer-flow-web-app with your preferred container name
docker run -d -t -p 3000:3000 --env-file .env --name deer-flow-web-app deer-flow-web

# stop the server
docker stop deer-flow-web-app
```

### Docker Compose

你也可以使用 Docker Compose 设置此项目：

```bash
# building docker image
docker compose build

# start the server
docker compose up
```

## 许可证

本项目为开源项目，采用 [MIT 许可证](../LICENSE)。

## 致谢

我们衷心感谢开源社区做出的宝贵贡献。DeerFlow 构建于这些杰出项目之上：

我们尤其要向以下各方致以衷心感谢：

- [Next.js](https://nextjs.org/)，感谢他们提供出色的框架
- [Shadcn](https://ui.shadcn.com/)，其简约组件为我们的 UI 提供支持
- [Zustand](https://zustand.docs.pmnd.rs/)，凭借其出色的状态管理功能
- [Framer Motion](https://www.framer.com/motion/)，感谢他们提供出色的动画库
- [React Markdown](https://www.npmjs.com/package/react-markdown)，提供卓越的 Markdown 渲染能力和高度可定制性
- 最后但同样重要的是，特别感谢 [SToneX](https://github.com/stonexer) 为 [逐 token 视觉效果](./src/core/rehype/rehype-split-words-into-spans.ts) 做出的杰出贡献

这些优秀项目构成了 DeerFlow 的核心支柱，彰显了开源协作的变革力量。
