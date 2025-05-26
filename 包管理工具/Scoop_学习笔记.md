# 🧰 Scoop 学习笔记

> Scoop 是 Windows 上的命令行包管理器，类似 Linux 的 `apt` 或 macOS 的 `brew`。可轻松安装/管理命令行程序和开发工具，无需管理员权限。

---

## 📌 安装 Scoop

### 1. 打开 PowerShell（非管理员身份）

### 2. 设置执行策略（只需一次）

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### 3. 安装 Scoop

```powershell
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

---

## 🔧 Scoop 基本命令

| 命令                         | 说明                  |
| ---------------------------- | --------------------- |
| `scoop install <软件名>`   | 安装软件              |
| `scoop uninstall <软件名>` | 卸载软件              |
| `scoop list`               | 查看已安装软件        |
| `scoop update`             | 更新 Scoop 和 buckets |
| `scoop update <软件名>`    | 更新指定软件          |
| `scoop search <关键词>`    | 搜索软件              |
| `scoop info <软件名>`      | 查看软件信息          |
| `scoop cleanup`            | 清理旧版本和缓存      |

## 🔧Scoop命令行帮助翻译

```shell
alias      管理独家别名
bucket     管理 Scoop 桶
cache      显示或清除下载缓存
cat        显示特定清单的内容。
checkup    检查潜在问题
cleanup    通过删除旧版本来清理应用程序
config     获取或设置配置值
create     创建自定义应用程序清单
depends    列出应用程序的依赖项,按它们将被安装的顺序
download   在缓存文件夹中下载应用程序并验证哈希值
export     以 JSON 形式导出已安装的应用程序、存储桶(以及可选配置)
help       显示对命令的帮助
hold       持有一个应用程序禁用更新
home       打开应用主页
import     以 JSON 格式从 Scoopfile 导入应用程序、存储桶和配置
info       显示有关应用程序的信息
install    安装应用程序
list       列出已安装的应用程序
prefix     返回路径到指定的应用程序
reset      重置一个应用程序来解决冲突
search     搜索可用的应用程序
shim       操纵 Scoop shims
status     显示状态并检查新的应用版本
unhold     取消应用程序以启用更新
uninstall  卸载一个应用程序
update     更新应用程序,或Scoop本身
virustotal 在 virustotal.com 上查找应用的哈希值或 url
which      找到 shim/executable(类似于 Linux 上的 'which')
```

---

## 🪣 管理 bucket（软件仓库）

| 命令                        | 说明                      |
| --------------------------- | ------------------------- |
| `scoop bucket list`       | 查看当前添加的 bucket     |
| `scoop bucket add <名称>` | 添加 bucket（如：extras） |
| `scoop bucket rm <名称>`  | 删除 bucket               |

### 常用 buckets：

```bash
scoop bucket add extras        # 图形化工具
scoop bucket add nerd-fonts    # 编程字体
scoop bucket add versions      # 多版本工具
scoop bucket add java          # Java 相关工具
```

---

## 📦 推荐安装软件清单

```bash
scoop install git
scoop install 7zip
scoop install python
scoop install nodejs-lts
scoop install neovim
scoop install everything
scoop install sudo
scoop install aria2    # 多线程下载支持
```

---

## ⚙️ Scoop 配置命令

| 命令                                     | 说明                  |
| ---------------------------------------- | --------------------- |
| `scoop config aria2-enabled true`      | 启用 aria2 多线程下载 |
| `scoop config SCOOP_REPO "<镜像地址>"` | 设置 scoop 源仓库     |
| `scoop cache rm *`                     | 清除所有缓存包        |

---

## 🧪 示例：一键初始化开发环境

```powershell
scoop bucket add extras
scoop install git python nodejs-lts neovim 7zip everything
```

---

## 🧯 常见问题

### ❓ 安装失败？

- 确保使用的是非管理员 PowerShell
- 设置了执行策略 `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`
- 网络问题建议使用国内镜像

---

## 🔗 官网与资源

- 官网：https://scoop.sh/
- GitHub：https://github.com/ScoopInstaller/Scoop
- 中文镜像站：https://mirror.nju.edu.cn/scoop/

---
