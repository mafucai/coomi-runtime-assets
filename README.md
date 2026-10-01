# Coomi Runtime V2 assets

Coomi Runtime V2 内置环境资产（ARM64），用于 CoomiDev APK 离线打包。

## 资产

| 文件 | 大小 | SHA256 |
|---|---|---|
| `proot-host-arm64.tar.gz` | 119,181 | `77eb98f3d528bb83db0bba6fec703f577724dd7fefcaf8cafc34607eaac60f0e` |
| `ubuntu-noble-arm64.tar.gz` | 311,219,155 | `b21e06186c0ad6bfaca7e6d6ff27b0e4d2e592a320e98b2a20d32ab9a54e8769` |
| `runtime-v2-manifest.json` | 1,028 | — |

`runtime_version`: `ubuntu-noble-20260907-proot-5.1.107.91`
`proot_commit`: `61681c6481197e3c0cec6726075053adb740f235`

## 来源

从官方 Coomi v1.4.8 APK 中提取（`assets/runtime-v2/`），SHA256 已逐字节校验与 manifest 一致。

- APK 来源：<https://github.com/TensorHub-ORG/Coomi/releases/tag/v1.4.8>
- 上游项目：<https://github.com/TensorHub-ORG/Coomi>（Apache-2.0）
- PRoot：GPL-2.0-or-later

## 用途

填入 Coomi 源码树根目录的 `runtime-v2-dist/`，使 Gradle 任务 `stageCoomiRuntimeV2` 校验通过，从而把内置环境打进 CoomiDev APK。

```sh
mkdir -p runtime-v2-dist
curl -L -o runtime-v2-dist/proot-host-arm64.tar.gz \
  https://github.com/mafucai/coomi-runtime-assets/releases/download/runtime-v2-ubuntu-noble-20260907/proot-host-arm64.tar.gz
curl -L -o runtime-v2-dist/ubuntu-noble-arm64.tar.gz \
  https://github.com/mafucai/coomi-runtime-assets/releases/download/runtime-v2-ubuntu-noble-20260907/ubuntu-noble-arm64.tar.gz
```

## 校验

```sh
sha256sum runtime-v2-dist/*.tar.gz
```

## 声明

本仓库仅为官方开源项目的构建资产镜像，便于个人 fork 的 CI 复用；版权与许可归属上游 Coomi 项目及 PRoot 项目。
