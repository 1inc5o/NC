# NC (Need Check)

<img width="1502" height="1304" alt="image" src="https://github.com/user-attachments/assets/9b2cfb06-b51e-4937-9fa8-58dc619404d7" />

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey.svg)
![Build](https://img.shields.io/badge/build-Electron%20%2B%20Go-informational.svg)

NC（Need Check）是一款面向应急响应场景的本地排查工具：以“开箱即用”为目标，把进程/网络/日志/痕迹等常见排查入口集中到一个界面里，帮助分析师更快定位异常与攻击链线索。

**祝每一个应急人员可以按时下班。**

## 特性

- **进程与模块**：进程列表、父子关系（进程树）、模块/DLL 关联、可执行文件签名信息
- **网络排查**：连接与进程关联、可疑外联辅助定位、DNS 实时监控（需要权限）
- **日志分析**：Windows 事件日志（EVTX）场景化扫描与威胁摘要、Web 访问日志攻击特征识别
- **主机体检**：用户、服务、计划任务、启动项、已装软件等基线信息聚合
- **文件与痕迹**：关键路径快速搜索、预设场景（如 WebShell/近期可执行文件）、常见取证痕迹（Prefetch/UserAssist/Recent 等）
- **本地优先**：默认仅本机处理与展示，不依赖云端

## 快速开始

### 运行（Windows 便携版）

1. 从 GitHub Releases 下载 `NC-x.y.z-win-x64.exe`
2. 建议 **以管理员身份运行**（部分能力依赖权限：系统日志读取、DNS 监控、部分进程信息等）
3. 打开后可先进入 `健康检查`，确认关键接口均为 `OK`

### 推荐排查路径

- **先看进程**：关注未签名/路径异常/父子关系异常的进程
- **再看网络**：重点关注连接公网 IP 的非浏览器进程与异常端口
- **再看日志**：对安全/系统日志做场景扫描，结合威胁摘要回溯攻击动作
- **最后补痕迹与文件**：按时间范围和关键词做落地文件与持久化线索定位

## 功能一览

| 模块 | 你能做什么 | 典型用途 |
|---|---|---|
| 进程信息 | 进程树、命令行、签名、模块 | 定位可疑父子链、注入/劫持线索 |
| 网络信息 | 连接与进程关联、DNS 监控 | 找 C2 外联、隧道、异常解析 |
| 日志分析 | EVTX 场景扫描、威胁摘要、Web 日志攻击识别 | 攻击链回溯、爆破/横移/持久化线索 |
| 主机信息 | 用户/服务/计划任务/启动项/软件 | 盘点持久化、异常账户、可疑服务 |
| 活动痕迹 | Prefetch/UserAssist/Recent 等 | 还原执行痕迹与时间线 |
| 文件搜索 | 预设与自定义规则 | WebShell、近期落地、可疑大文件 |
<img width="1081" height="688" alt="image" src="https://github.com/user-attachments/assets/03d36697-35a7-4769-aa5b-37691465034b" />
<img width="2164" height="1270" alt="image" src="https://github.com/user-attachments/assets/3f585103-40cc-4469-9d9c-c012eacaadb8" />
<img width="2162" height="1312" alt="image" src="https://github.com/user-attachments/assets/ec8f1677-a1c4-47ba-869a-15d8d8f386de" />
<img width="2188" height="1180" alt="image" src="https://github.com/user-attachments/assets/cdb0d689-f1bb-4191-8173-7f496c23a49e" />
<img width="2140" height="710" alt="image" src="https://github.com/user-attachments/assets/98d6ba14-9930-45cb-b4f6-88a79b41ce7f" />
<img width="2150" height="1100" alt="image" src="https://github.com/user-attachments/assets/9a777ac9-412a-4566-9810-f67bcccf8ff6" />
<img width="2366" height="1248" alt="image" src="https://github.com/user-attachments/assets/c6751a87-1ceb-4dff-89f6-23c183b6958c" />
<img width="2176" height="868" alt="image" src="https://github.com/user-attachments/assets/30685fc9-4a77-4cd7-8ba5-7a8f830cfde6" />
<img width="2160" height="1276" alt="image" src="https://github.com/user-attachments/assets/8cf6612c-792e-42ed-9521-e7f324f57488" />

## 项目结构

- `cmd/NC`：Go 后端入口
- `internal/server`：HTTP API（供 Electron 前端调用）
- `internal/loganalysis`：日志分析能力（EVTX/Web 日志等）
- `electron-app`：Electron 前端与打包配置


## 说明与限制

- 部分能力目前主要面向 Windows；macOS/Linux暂未实现
- 杀毒软件可能对日志读取、注入扫描等行为产生误报，建议在授权环境添加白名单
- 本工具用于授权应急响应与安全研究，请勿用于非法用途

## 致谢

- Electron
- Go
- `gopsutil`
- `golang-evtx`
- Zircolite / Chainsaw 规则生态（用于检测思路与规则参考）
- Hawkeye 界面、功能设计参考
- LogForensics web日志检测

## 反馈与贡献

- Issue：欢迎提交 bug、功能建议与样本日志（注意脱敏）
- PR：欢迎贡献规则、解析器与 UI 改进

---

License: MIT  \
Author: 1inc50
