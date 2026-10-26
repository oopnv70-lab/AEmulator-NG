# AEmulator-NG

**本仓库不包含 AEmulator 源码。** 它只是一个 CI 执行仓：存放 GitHub Actions 工作流，构建时从
[oopnv70-lab/AEmulator](https://github.com/oopnv70-lab/AEmulator) 拉取源码并编译 APK。

---

## 1. 来源与授权链

| 层级 | 项目 | 角色 | 许可证 |
|---|---|---|---|
| 上游原仓库 | [uxazu/AEmulator](https://github.com/uxazu/AEmulator) | AEmulator 直接上游 | GNU GPL v3.0 |
| 更早的源头 | [Istratii-tech/SENSES](https://github.com/Istratii-tech/SENSES) | 原始引擎（SENSES Emulator） | GNU GPL v2.0 |
| 构建源码 | [oopnv70-lab/AEmulator](https://github.com/oopnv70-lab/AEmulator) | 本工作流实际编译的代码 | GNU GPL v3.0 |
| 本仓库 | oopnv70-lab/AEmulator-NG | 仅含 CI 配置 | GNU GPL v3.0 |

**本仓库不是原创项目，不对 AEmulator 主张任何著作权。** 原始架构与绝大部分代码由上游作者创作。
原始引擎作者联系方式：[t.me/istratii_tech1](https://t.me/istratii_tech1)。

本仓库与上游作者、与任何固件厂商（HTC、三星、小米、荣耀等）**均无关联，未获其授权或背书**。

---

## 2. 为什么要单独开这个仓库

`oopnv70-lab/AEmulator` 是 GitHub fork。由于 Actions 用量过大，GitHub 已停止在该 fork 上运行工作流，页面原文：

> Workflows are not currently being run on this fork due to the scale of GitHub Actions usage. A repository maintainer can choose to re-enable these.

该限制无法通过 API 解除（`PUT /actions/permissions` 与 `PUT /actions/workflows/{id}/enable` 均返回 `204`，但 `POST .../dispatches` 仍返回 `422 Actions has been disabled for this repository`）。因此新建本仓库（普通仓库，非 fork）承载 CI，源码仍留在原仓库，两边不重复。

---

## 3. 用法

- 向本仓库 `main` 推送，自动触发构建
- 或在 Actions 页面手动 Run workflow
- 产物：`AEmulator-Debug-APKs`，保留 7 天

构建产物**包含完整的 LICENSE 与 NOTICE 文本**（工作流会把它们一并放进 artifact 目录），以满足 GPL-3.0 与 Apache-2.0 随分发附带许可证的要求。

---

## 4. 许可证与第三方组件

- 本项目许可证：[GNU GPL v3.0](LICENSE)
- 第三方组件、二进制来源、已知合规缺口：见 [NOTICE.md](NOTICE.md)

**重要提示**：构建产出的 APK 内含修改版 QEMU（GPLv2）与 SwiftShader（Apache-2.0）等预编译二进制。
其对应源码的提供义务由分发行为触发。当前状态与补齐步骤见 [NOTICE.md](NOTICE.md) 与上游仓库的 `docs/COMPLIANCE.md`。

---

## 5. 修改声明（GPL-3.0 §5(a)）

本仓库工作流编译的代码是 `oopnv70-lab/AEmulator` 相对上游 `uxazu/AEmulator` 的**修改版本**，
修改内容以该仓库的 git 提交历史完整记录。主要方向为使 Honor MagicOS 12（API 31）等固件可在
本引擎上启动，详见该仓库 `README.md` 的「本分支做了什么」一节。

---

## 6. 生成式 AI 参与说明

本仓库的配置文件与上游仓库的部分提交在 AI 辅助下完成，经人工确认后提交。AI 工具不对这些内容主张版权。