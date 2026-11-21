# yunjianmanbu

**Pilot** —— 跑在你自己电脑上的本地优先自主编程 Agent，外加它配套的两个手机端和一个自建中继。
四个仓库、四个控制方向，共用一套权限模型和一份脱敏审计日志。

[English](README.md) | **中文**

**官网与下载：** <https://pilot.medpilot.cc/zh.html> —— 一页放齐所有安装包。
**文档：** [Wiki · 中文](https://github.com/yunjianmanbu/pilot/wiki/Home.zh-CN) · [用途边界](https://github.com/yunjianmanbu/pilot/blob/main/RESPONSIBLE_USE.md)

## 四个仓库

| 仓库 | 是什么 | 谁控制谁 | 版本 |
| --- | --- | --- | --- |
| **[pilot](https://github.com/yunjianmanbu/pilot)** | 桌面 Agent：读你的代码、跑命令、改文件、验证结果。Electron + React，DeepSeek 或任何 OpenAI 兼容模型，免登录、无云数据库。 | 人 → 电脑 | v0.1.88 |
| **[pilot-link](https://github.com/yunjianmanbu/pilot-link)** | 手机端（uni-app），把手机变成这台桌面 Agent 的遥控器：发指令、看回答、批准或拒绝工具调用。 | 手机 → 电脑 | v1.1.4 |
| **[pilot-client](https://github.com/yunjianmanbu/pilot-client)** | 反方向：电脑看屏幕、点屏幕、读通知与文件，每一个动作都过 12 类能力目录与审计。**Beta**：需要 Android 系统服务的能力仍明确返回 `not_granted`。 | 电脑 → 手机 | beta · v1.0.5 |
| **[pilot-connector](https://github.com/yunjianmanbu/pilot-connector)** | 你自己部署的中继与连接器，配对与命令流量不经过任何别人的服务器。项目不提供公共中继。 | 手机 ↔ 电脑 ↔ 桌面 | v0.2.3 |

```
 手机（Pilot Link）──┐
                     ├── 自建中继（pilot-connector）
 手机（Pilot Client）┘            │
                                  │  ECDH P-256 + AES-256-GCM，逐配对密钥
                                  ▼
                    桌面 Agent（Pilot）—— 你的文件、你的模型 Key
```

## 从哪进

| 你想做的事 | 去处 |
| --- | --- |
| 在自己电脑上试这个 Agent | [pilot README · 快速开始](https://github.com/yunjianmanbu/pilot/blob/main/README.zh-CN.md#快速开始) |
| 用手机指挥它 | [pilot README · 手机连接](https://github.com/yunjianmanbu/pilot/blob/main/README.zh-CN.md#手机连接) |
| 在服务器上跑无界面模式，用浏览器当控制台 | [pilot README · 服务器模式](https://github.com/yunjianmanbu/pilot/blob/main/README.zh-CN.md#服务器模式) |
| 不经第三方服务器配对手机 | [pilot-connector](https://github.com/yunjianmanbu/pilot-connector) |
| 装之前先看清权限关卡 | [pilot README · 安全](https://github.com/yunjianmanbu/pilot/blob/main/README.zh-CN.md#安全) · [RESPONSIBLE_USE.md](https://github.com/yunjianmanbu/pilot/blob/main/RESPONSIBLE_USE.md) |
| 每个版本改了什么 | [pilot](https://github.com/yunjianmanbu/pilot/blob/main/CHANGELOG.zh-CN.md) · [pilot-link](https://github.com/yunjianmanbu/pilot-link/blob/main/CHANGELOG.zh-CN.md) · [pilot-client](https://github.com/yunjianmanbu/pilot-client/blob/main/CHANGELOG.zh-CN.md) · [pilot-connector](https://github.com/yunjianmanbu/pilot-connector/blob/main/CHANGELOG.zh-CN.md) |

## 三条不让步的默认值

1. **不指向模型就什么都不外传。** 没有账号体系、没有云数据库、没有遥测；你填的 API Key 只存在本机配置里。
2. **每个动作都要过关，被拒绝的也留痕。** 危险命令在策略上限之上、手机端 L2 以上动作要机上确认，
   审计日志里的剪贴板内容、短信正文、文件路径、手机号一律脱敏成长度。
3. **只用于你拥有、或已获设备所有者明确授权的设备。** 隐蔽监控、群控养号、冒充客服代操作不在支持范围内，
   项目公开表态见 [RESPONSIBLE_USE.md](https://github.com/yunjianmanbu/pilot/blob/main/RESPONSIBLE_USE.md)。

四个仓库都是 Apache-2.0。问题与想法请走
[Issues](https://github.com/yunjianmanbu/pilot/issues/new/choose) 与
[Discussions](https://github.com/yunjianmanbu/pilot/discussions)；安全问题按
[SECURITY.md](https://github.com/yunjianmanbu/pilot/blob/main/SECURITY.md) 报。
