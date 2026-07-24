# Tsuki

> [!WARNING]
> **Tsuki** 是 [Paru](https://github.com/Morganamilo/paru)（功能丰富的 AUR 助手）的一个分支。本项目对原始 Paru 代码库进行了扩展和修改。
> 目前 Tsuki 尚未准备好投入实际使用。

功能丰富的 AUR 助手

## 描述

Tsuki 是一个标准的 pacman 包装型 AUR 助手，功能丰富且交互极少。

## 特色

Tsuki 添加了部分官方（可能）未在计划中的功能：

- 电脑中存在 opencode, Tsuki 会调用 opencode 审核 PKGBUILD
- 使用`--sudopassword <密码>`可以在调用sudo时通过-S参数指定密码。**该功能专为部分自动化脚本设计，非必要请勿使用**

## 安装

目前 Tsuki 尚未准备好投入实际使用。

```
sudo pacman -S --needed base-devel
git clone https://aur.archlinux.org/tsuki.git
cd tsuki
makepkg -si
```

## 贡献

参见 [CONTRIBUTING.md](./CONTRIBUTING.md)。

## 通用提示

- **手册页**：有关 tsuki 的选项和配置文件的文档，请分别参见 `tsuki(8)` 和 `tsuki.conf(5)`。

- **颜色**：Tsuki 仅在 pacman 启用了颜色的情况下启用颜色。请在 `pacman.conf` 中启用 `color`。

- **基于文件的审查**：要获得更高级的审查流程，请在 `tsuki.conf` 中使用你喜爱的文件管理器启用 `FileManager`。

- **翻转搜索顺序**：要使搜索结果从底部开始向上显示，请在 `tsuki.conf` 中启用 `BottomUp`。

- **编辑 PKGBUILD**：编辑 PKGBUILD 时，你可以提交更改以使其永久生效。当包升级时，`git` 会尝试将你的更改与上游的更改合并。

- **PKGBUILD 语法高亮**：你可以安装 [`bat`](https://github.com/sharkdp/bat) 以在 PKGBUILD 审查过程中启用语法高亮。

- **跟踪 -git 包**：Tsuki 通过监控上游仓库来跟踪 -git 包。Tsuki 只能跟踪它自己安装的包。运行 `tsuki --gendb` 可以让 tsuki 识别那些并非由它安装的包。

## 示例

`tsuki <target>` — 交互式搜索并安装 `<target>`。

`tsuki` — `tsuki -Syu` 的别名。

`tsuki -S <target>` — 安装指定包。

`tsuki -Sua` — 升级 AUR 包。

`tsuki -Qua` — 列出可用的 AUR 更新。

`tsuki -G <target>` — 下载 `<target>` 的 PKGBUILD 及相关文件。

`tsuki -Gp <target>` — 打印 `<target>` 的 PKGBUILD。

`tsuki -Gc <target>` — 打印 `<target>` 的 AUR 评论。

`tsuki --gendb` — 生成用于跟踪 `*-git` 包的开发数据库。仅在你首次开始使用 tsuki 时需要。

`tsuki -Bi .` — 构建并安装当前目录下的 PKGBUILD。

## 调试

Tsuki 不是官方工具。如果 tsuki 无法构建某个包，你应首先检查 makepkg 能否成功构建该包。如果不能，则应向维护者报告问题。否则，这很可能是 tsuki 的问题，应在此处报告。
