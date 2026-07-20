# Pinky

> [!WARNING]
> **Pinky** 是 [Paru](https://github.com/Morganamilo/paru)（功能丰富的 AUR 助手）的一个分支。本项目对原始 Paru 代码库进行了扩展和修改。
> 目前 Pinky 尚未准备好投入实际使用。

功能丰富的 AUR 助手

## 描述

Pinky 是一个标准的 pacman 包装型 AUR 助手，功能丰富且交互极少。

## 特色

Pinky 添加了部分官方（可能）未在计划中的功能：

- 电脑中存在 opencode, Pinky 会调用 opencode 审核 PKGBUILD
- 使用`--sudopassword <密码>`可以在调用sudo时通过-S参数指定密码。**该功能专为部分自动化脚本设计，非必要请勿使用**

## 安装

目前 Pinky 尚未准备好投入实际使用。

```
sudo pacman -S --needed base-devel
git clone https://aur.archlinux.org/pinky.git
cd pinky
makepkg -si
```

## 贡献

参见 [CONTRIBUTING.md](./CONTRIBUTING.md)。

## 通用提示

- **手册页**：有关 pinky 的选项和配置文件的文档，请分别参见 `pinky(8)` 和 `pinky.conf(5)`。

- **颜色**：Pinky 仅在 pacman 启用了颜色的情况下启用颜色。请在 `pacman.conf` 中启用 `color`。

- **基于文件的审查**：要获得更高级的审查流程，请在 `pinky.conf` 中使用你喜爱的文件管理器启用 `FileManager`。

- **翻转搜索顺序**：要使搜索结果从底部开始向上显示，请在 `pinky.conf` 中启用 `BottomUp`。

- **编辑 PKGBUILD**：编辑 PKGBUILD 时，你可以提交更改以使其永久生效。当包升级时，`git` 会尝试将你的更改与上游的更改合并。

- **PKGBUILD 语法高亮**：你可以安装 [`bat`](https://github.com/sharkdp/bat) 以在 PKGBUILD 审查过程中启用语法高亮。

- **跟踪 -git 包**：Pinky 通过监控上游仓库来跟踪 -git 包。Pinky 只能跟踪它自己安装的包。运行 `pinky --gendb` 可以让 pinky 识别那些并非由它安装的包。

## 示例

`pinky <target>` — 交互式搜索并安装 `<target>`。

`pinky` — `pinky -Syu` 的别名。

`pinky -S <target>` — 安装指定包。

`pinky -Sua` — 升级 AUR 包。

`pinky -Qua` — 列出可用的 AUR 更新。

`pinky -G <target>` — 下载 `<target>` 的 PKGBUILD 及相关文件。

`pinky -Gp <target>` — 打印 `<target>` 的 PKGBUILD。

`pinky -Gc <target>` — 打印 `<target>` 的 AUR 评论。

`pinky --gendb` — 生成用于跟踪 `*-git` 包的开发数据库。仅在你首次开始使用 pinky 时需要。

`pinky -Bi .` — 构建并安装当前目录下的 PKGBUILD。

## 调试

Pinky 不是官方工具。如果 pinky 无法构建某个包，你应首先检查 makepkg 能否成功构建该包。如果不能，则应向维护者报告问题。否则，这很可能是 pinky 的问题，应在此处报告。
