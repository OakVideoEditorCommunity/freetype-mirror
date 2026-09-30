# freetype-mirror

[English](#english) | [中文](#中文)

## 中文

本仓库是 **FreeType 发布包的镜像**，不是 FreeType 项目本身，也与 FreeType 团队无关。

### 为什么存在

Oak 的 CI（以及本地构建脚本 `tooling/ffmpeg/build-deps.sh`）需要从
`download.savannah.gnu.org` 下载 freetype 源码包，但该站点访问不稳定，
经常因网络问题导致构建失败。本仓库通过 GitHub Actions 从官方源拉取
tarball 并以 GitHub Release 的形式重新发布，构建脚本改为从 GitHub
下载，利用 GitHub 的 CDN 获得稳定、快速的下载。

### 包含的版本

| 版本 | 上游地址 | 镜像 Release |
| ---- | -------- | ------------ |
| 2.13.3 | <https://download.savannah.gnu.org/releases/freetype/freetype-2.13.3.tar.xz> | <https://github.com/OakVideoEditorCommunity/freetype-mirror/releases/tag/v2.13.3> |

### 如何镜像新版本

手动触发 **Mirror freetype release** workflow（Actions 页面），输入版本号即可。
workflow 会从 savannah 官方镜像重定向器
（`download-mirror.savannah.gnu.org`）下载并校验 tarball，
然后创建标签为 `v<版本号>` 的 Release 并附带该 tarball。

### 完整性说明

tarball 内容未做任何修改。如需校验，可将 Release 附件与上游
`download.savannah.gnu.org` 的同名文件做 SHA-256 比对。

## English

This repository is a **mirror of FreeType release tarballs**. It is not the
FreeType project itself and is not affiliated with the FreeType team.

### Why it exists

Oak's CI (and the local build script `tooling/ffmpeg/build-deps.sh`)
downloads the freetype source tarball from `download.savannah.gnu.org`,
which is unreliable and often fails. A GitHub Actions workflow here pulls
the tarball from the upstream mirror redirector and republishes it as a
GitHub Release, so builds download from GitHub's CDN instead.

### Mirroring a new version

Manually dispatch the **Mirror freetype release** workflow with the version
number. The workflow downloads the tarball from
`download-mirror.savannah.gnu.org`, verifies it, and creates a release
tagged `v<version>` with the tarball attached.

### Integrity

Tarballs are published unmodified. To verify, compare the SHA-256 of a
release asset with the same file on `download.savannah.gnu.org`.

FreeType is distributed under the FreeType License (FTL) / GPLv2; see the
tarball itself for details.
