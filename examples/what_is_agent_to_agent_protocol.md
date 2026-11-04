# Google 智能体间协议报告

## 要点

-   Google 的 Agent2Agent（A2A）协议对 AI 智能体之间的通信进行标准化，以促进不同系统间的协作。
-   A2A 支持在智能体之间交换消息，以共享上下文、指令和成果物。
-   该协议通过为智能体提供网络层，与 Anthropic 的模型上下文协议（MCP）形成互补。
-   A2A 允许智能体协商内容格式，并支持 iframe 和视频等多种媒体类型。
-   Google 计划将 A2A 打造为一个开放、由社区驱动的项目，以促进创新和采用。
-   行业专家预计，A2A 将通过简化集成和数据交换来加速 AI 的采用。

---

## 概述

Google 的 Agent2Agent（A2A）协议旨在建立一种标准化方式，使 AI 智能体无论来源、框架或所在位置如何，都能彼此通信。该计划致力于促进 AI 智能体之间的无缝协作和集体智能，从而提升智能体解决方案的效能。A2A 作为网络层运行，与 Anthropic 的模型上下文协议（MCP）等其他协议互补，推动形成更加统一的 AI 智能体生态系统。

---

## 详细分析

### 目的与设计

A2A 通过为 AI 智能体提供一种通用语言，解决不同 AI 系统的集成难题。它支持这些智能体共享上下文、回复、成果物和用户指令，从而促进协作式问题解决。A2A 的设计允许智能体协商 iframe、视频和网页表单等内容格式，以支持灵活的用户体验。

### 技术层面

该协议在消息中使用“部分（parts）”，即指定了内容类型的完整内容单元，使智能体之间能够协商所需的正确格式。A2A 基于 HTTP、SSE 和 JSON-RPC 等现有标准构建。

### 社区与行业影响

Google 对 A2A 的愿景是创建一个开放、由社区驱动的项目，鼓励开源社区贡献和更新。来自 Deloitte、Accenture、EPAM 和 New Relic 等公司的行业专家认为，A2A 将通过简化集成、促进数据交换并推动形成更加统一的 AI 智能体生态系统，加速 AI 的采用。LangChain 也表示有兴趣与 Google Cloud 就这一共享协议开展合作。

### 与 MCP 的关系

A2A 与 Anthropic 的模型上下文协议（MCP）形成互补。A2A 为智能体通信提供网络层，而 MCP 则充当插件系统，使智能体能够访问工具、上下文和数据。

---

## 主要引用

-   [Agent2Agent 协议（A2A）发布公告](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/)

-   [使用 Vertex AI 构建和管理多系统智能体 - Google Cloud](https://cloud.google.com/blog/products/ai-machine-learning/build-and-manage-multi-system-agents-with-vertex-ai)

-   [Google 刚刚推出 Agent2Agent：面向 AI 智能体的开放协议……](https://www.maginative.com/article/google-just-launched-agent2agent-an-open-protocol-for-ai-agents-to-work-directly-with-each-other/)

-   [智能体 AI 协议：Google 全新 A2A 加入热门 MCP 生态](https://virtualizationreview.com/articles/2025/04/09/protocols-for-agentic-ai-googles-new-a2a-joins-viral-mcp.aspx)

-   [Google 的 Agent2Agent 互操作协议旨在实现标准化……](https://venturebeat.com/ai/googles-agent2agent-interoperability-protocol-aims-to-standardize-agentic-communication/)

-   [认识 Google A2A：将彻底改变多智能体系统的协议……](https://medium.com/@the_manoj_desai/meet-google-a2a-the-protocol-that-will-revolutionize-multi-agent-ai-systems-80d55a4583ed)

-   [Google 的 Agent2Agent 协议帮助 AI 智能体相互交流](https://thenewstack.io/googles-agent2agent-protocol-helps-ai-agents-talk-to-each-other/)