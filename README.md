# AEmulator-NG

CI 执行仓。源码在 [oopnv70-lab/AEmulator](https://github.com/oopnv70-lab/AEmulator)（fork 自 [uxazu/AEmulator](https://github.com/uxazu/AEmulator)）。

## 为什么有这个仓库

`oopnv70-lab/AEmulator` 是 GitHub fork，由于 Actions 用量过大被 GitHub 停跑：

> Workflows are not currently being run on this fork due to the scale of GitHub Actions usage. A repository maintainer can choose to re-enable these.

API 无法解除该限制（`PUT /actions/permissions` 与 `PUT /workflows/{id}/enable` 均返回 204，但 dispatch 仍 422）。因此新建本仓库作为普通仓库（非 fork），仅存放 workflow，构建时 `actions/checkout` 直接拉取 `oopnv70-lab/AEmulator` 的 `main` 分支源码。

## 用法

- push 到本仓库 `main` 即触发构建
- 或在 Actions 页面手动 Run workflow
- 产物为 `AEmulator-Debug-APKs`，保留 7 天

## 上游

- 上游原仓库：https://github.com/uxazu/AEmulator
- 构建源码仓库：https://github.com/oopnv70-lab/AEmulator
