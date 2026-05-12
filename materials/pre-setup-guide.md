# AI Agent Hands on Lab — 课前准备指南

> **目标受众**：中欧商学院MBA学员
> **核心工具**：Claude Code + CC Switch + 阿里百炼
> **请在工作坊开始前完成以下准备，预计耗时30-40分钟**

---

## 一、安装 Claude Code

Claude Code 是 Anthropic 推出的 AI 编程助手，也是本次工作坊的核心交互工具。它能自主执行多步骤任务（读写文件、运行代码、网络搜索等），是理解 AI Agent 工作原理的最佳入口。

### 系统要求

- **macOS**: macOS 12 (Monterey) 及以上
- **Windows**: Windows 10 及以上（需安装 WSL2 + Ubuntu）
- **Linux**: Ubuntu 22.04+ / Debian 11+ / Fedora 34+

### 安装步骤

#### macOS / Linux

打开终端，执行以下命令：

```bash
# 使用 npm 全局安装（推荐）
npm install -g @anthropic-ai/claude-code

# 验证安装
claude --version
```

如果看到版本号（如 `0.2.35`），说明安装成功。

#### Windows

Windows 用户需要先安装 WSL2（Windows Subsystem for Linux）：

1. 以管理员身份打开 PowerShell，执行：
   ```powershell
   wsl --install
   ```
2. 重启电脑，按提示完成 Ubuntu 初始化设置
3. 进入 WSL2 的 Ubuntu 环境，执行上面的 npm 安装命令

### 首次运行

安装完成后，在终端输入：

```bash
claude
```

首次运行会要求登录 Anthropic 账号。请使用您已有的 Anthropic 账号，或根据提示注册一个。

> **注意**：Claude Code 默认使用 Anthropic 官方 API。在正式工作坊中，我们会通过 CC Switch 将其切换到阿里百炼，以获得更稳定的国内访问体验。

---

## 二、安装 CC Switch

CC Switch 是一个桌面应用，用于统一管理 Claude Code、Codex、Gemini CLI 等工具的 API 供应商配置。它让我们可以在不同模型供应商之间一键切换，无需手动修改配置文件。

### 下载安装

#### macOS（推荐 Homebrew）

```bash
brew tap farion1231/ccswitch
brew install --cask cc-switch
```

安装完成后，在 Launchpad 或 Spotlight 中搜索 "CC Switch" 即可打开。

#### Windows

1. 访问 CC Switch 的 GitHub Releases 页面：
   https://github.com/farion1231/cc-switch/releases
2. 下载最新版本的 `CC-Switch-v{版本号}-Windows.msi`
3. 双击安装

#### Linux

1. 访问上述 Releases 页面
2. 根据您的发行版选择：
   - Ubuntu/Debian: `.deb` 包
   - Fedora/RHEL: `.rpm` 包
   - 其他: `.AppImage` 通用包

### 首次启动

打开 CC Switch 后：

1. 点击左侧 Claude Code 标签
2. 点击 "添加供应商"
3. 选择 "自定义" 或 "官方登录"
4. 先保留默认设置，工作坊现场我们会统一配置阿里百炼

> **提示**：CC Switch 是本次工作坊的"配置中枢"。即使您现在没完全搞懂，只要安装成功即可，现场会有详细演示。

---

## 三、申请阿里百炼 API 账号

阿里百炼是阿里云推出的大模型 API 平台，提供通义千问等模型的稳定访问。在国内网络环境下，它是 Claude Code 的可靠后端。

### 注册步骤

1. 访问阿里百炼官网：
   https://www.alibabacloud.com/help/zh/model-studio/getting-started/what-is-model-studio

2. 使用阿里云账号登录（如果没有，先注册阿里云账号）

3. 进入控制台，开通"模型服务"（通常有免费试用额度）

4. 创建 API Key：
   - 在控制台找到 "API Key 管理"
   - 点击 "创建 API Key"
   - 复制生成的 Key（以 `sk-` 开头），**妥善保存**

> **安全提醒**：API Key 相当于您的"密码"，不要分享到公开渠道。工作坊中我们会通过 CC Switch 本地管理，不会暴露在命令行中。

---

## 四、可选：安装 Node.js（如尚未安装）

Claude Code 和 CC Switch 都依赖 Node.js 环境。如果您的电脑尚未安装，请提前安装：

### macOS

```bash
# 使用 Homebrew 安装
brew install node

# 验证
node --version  # 应显示 v18.x 或更高
npm --version
```

### Windows

1. 访问 https://nodejs.org/
2. 下载 LTS 版本（左侧绿色按钮）
3. 双击安装包，按默认选项完成安装
4. 打开 PowerShell，执行 `node --version` 验证

### Linux

```bash
# Ubuntu/Debian
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs

# 验证
node --version
```

---

## 五、准备清单

工作坊开始前，请确认您已完成以下检查项：

- [ ] 电脑上已安装 Claude Code（`claude --version` 有输出）
- [ ] 电脑上已安装 CC Switch（能在桌面找到应用图标）
- [ ] 已注册阿里云/阿里百炼账号
- [ ] 已创建并保存阿里百炼 API Key（以 `sk-` 开头）
- [ ] 已安装 Node.js（`node --version` 显示 v18+）
- [ ] 确保电脑可连接互联网（工作坊需要访问 API）

---

## 六、常见问题

### Q1: 安装 Claude Code 时 npm 报错权限不足？

**macOS/Linux**: 尝试使用 npx 临时运行（无需全局安装）：
```bash
npx @anthropic-ai/claude-code
```

**Windows**: 以管理员身份运行 PowerShell，或检查 WSL2 是否正确安装。

### Q2: CC Switch 打开后界面空白？

尝试重启应用。如果仍有问题，访问 GitHub Issues 页面查看是否有已知问题：
https://github.com/farion1231/cc-switch/issues

### Q3: 阿里百炼 API Key 申请后没有额度？

新用户通常有免费试用额度。如果显示额度为0，可能是：
- 未完成实名认证（阿里云账号需要实名）
- 免费额度已用完（可充值少量金额用于工作坊，通常几元即可）

### Q4: 我是 Windows 用户，WSL2 安装太复杂？

如果实在无法在课前完成 WSL2 安装，可以考虑：
- 借用同学的 macOS 电脑组队
- 工作坊现场使用云端环境（如有提供）
- 提前联系助教寻求帮助

---

## 七、工作坊当天提醒

1. **请携带电脑**：本次工作坊全程上机实操，请务必携带已准备好的笔记本电脑
2. **提前15分钟到场**：用于现场环境检查和网络调试
3. **保存好 API Key**：工作坊中需要通过 CC Switch 配置阿里百炼，请确保您的 API Key 可随时访问（建议存在手机备忘录或密码管理器中）
4. **保持开放心态**：Agent 工具仍在快速迭代，今天学到的不仅是具体操作，更是"与 AI 协作"的思维框架

---

> **技术支持**：如果在课前准备中遇到任何问题，请在工作坊微信群中@助教，或在指定时间段参加线上答疑。
