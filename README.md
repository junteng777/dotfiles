# 🛠️ Dotfiles

> 个人开发环境配置文件集合，用于在不同机器间快速同步和恢复一致的编辑器体验。

## 📁 文件结构

```
dotfiles/
├── idea/
│   └── .ideavimrc          # JetBrains IdeaVim 配置
├── vscode/
│   ├── settings.json       # VS Code 全局设置
│   └── keybindings.json    # VS Code 自定义快捷键
├── mcp_config.json         # MCP 服务器配置（AI IDE 工具链）
└── .gitignore
```

## ⌨️ IdeaVim 配置

针对 JetBrains 全家桶（IntelliJ IDEA / GoLand / PyCharm 等）的 Vim 模拟配置。

**启用的插件：**
- `NERDTree` — 文件树导航
- `surround` — 快速包围文本
- `easymotion` — 快速跳转
- `sneak` — 双字符搜索跳转
- `highlightedyank` — 复制高亮
- `which-key` — 快捷键提示面板
- `keep-english-in-normal` — Normal 模式自动切换英文输入法

**核心键位映射：**

| 快捷键 | 模式 | 功能 |
|---|---|---|
| `<Space>` | Leader | Leader 键 |
| `jj` | Insert | 退出插入模式 |
| `H` / `L` | Normal | 行首 / 行尾 |
| `Y` | Normal | 复制到行尾 |
| `gh` | Normal | 显示错误描述 |
| `gq` | Normal | 格式化代码 |
| `<Leader>f` | Normal | 查找文件 |
| `<Leader>c` | Normal | 查找类 |
| `<Leader>a` | Normal | 查找操作 |
| `<Leader>s` | Normal | 查找符号 |
| `<Leader>i` | Normal | 跳转到实现 |
| `<Leader>b` | Normal | 跳转到声明 |
| `<Leader>w` | Normal | 保存全部 |
| `<Leader>q` | Normal | 关闭标签页 |
| `<Leader>n` | Normal | NERDTree 聚焦 |
| `<Leader>r` | Normal | 重命名元素 |

## 🆚 VS Code 配置

### 编辑器设置 (`settings.json`)

**基础配置：**
- 字体：`JetBrains Mono`（启用连字）
- 自动保存、平滑光标动画、相对行号
- 图标主题：`vscode-icons`
- 终端：Windows 默认 PowerShell，Linux 默认 Zsh

**Vim 插件 (`vscodevim.vim`)：**
- 启用 `surround`、`easymotion`、`sneak`、`camelCaseMotion`、`highlightedyank`
- 系统剪贴板集成
- Leader 键设为 `<Space>`
- 与 IdeaVim 保持一致的 `H`/`L`/`Y`/`jj` 映射

**语言格式化器：**

| 语言 | 格式化器 |
|---|---|
| Python | Ruff（保存时自动格式化 + 整理 import） |
| Java | Red Hat Java |
| HTML | VS Code 内置 |
| Vue | Volar |
| TypeScript / JavaScript | VS Code 内置 |
| JSON / JSONC | VS Code 内置 |
| XML | DotJoshJohnson.xml |
| CSS | VS Code 内置 |

**AI 助手集成：**
- GitHub Copilot
- CodeGeeX（中文偏好）
- 通义灵码 Lingma（简体中文）

**Java 开发环境：**
- JDK：Microsoft OpenJDK 21
- Maven：3.9.9

### 快捷键 (`keybindings.json`)

重新映射了以 `Ctrl+N` / `Ctrl+P` 为核心的导航逻辑，在所有上下文中保持一致：

| 快捷键 | 上下文 | 功能 |
|---|---|---|
| `Ctrl+P` | 编辑器 | 快速打开文件 |
| `Ctrl+N` / `Ctrl+P` | 建议列表 | 下一个 / 上一个建议 |
| `Ctrl+N` / `Ctrl+P` | Quick Open | 下一个 / 上一个文件 |
| `Ctrl+N` / `Ctrl+P` | Code Action | 下一个 / 上一个操作 |
| `Alt+I` | 全局 | 新建文件 |
| `Alt+B` | 全局 | 切换侧边栏 |
| `Alt+J` | 全局 | 切换底部面板 |
| `Ctrl+H` | 全局 | 聚焦编辑器 |
| `Ctrl+;` | 调试 | 启动 / 继续调试 |
| `Ctrl+'` | 调试 | 停止调试 |
| `Ctrl+Alt+;` | 调试 | 重启调试 |

## 🤖 MCP 配置

[Model Context Protocol](https://modelcontextprotocol.io/) 服务器配置，用于 AI 编码助手（如 Antigravity、VS Code Copilot Agent 等）。

**已配置的 MCP 服务器：**

| 服务器 | 运行方式 | 用途 |
|---|---|---|
| `filesystem` | npx | 文件系统读写操作 |
| `brave-search` | npx | Brave 搜索引擎集成 |
| `fetch` | uvx (Python) | 网页内容抓取 |
| `context7` | npx | 库/框架文档实时查询 |
| `github` | npx | GitHub API 操作 |
| `memory` | npx | 知识图谱 / 持久化记忆 |
| `sequential-thinking` | npx | 链式思考推理 |
| `puppeteer` | npx | 无头浏览器自动化 |
| `playwright` | npx | 浏览器自动化（更现代） |
| `excel` | npx | Excel 文件读写 |
| `sqlite` | uvx (Python) | SQLite 数据库操作 |
| `figma-dev-mode` | npx (mcp-remote) | Figma 设计稿集成 |

> ⚠️ **安全提示**：使用前请将 `mcp_config.json` 中的 API Key 和 Token 替换为你自己的凭据，切勿将敏感信息提交到公开仓库。

## 🚀 使用方法

### IdeaVim

将配置文件链接到用户目录：

```powershell
# Windows
Copy-Item .\idea\.ideavimrc $HOME\.ideavimrc
```

### VS Code

将配置复制到 VS Code 用户设置目录：

```powershell
# Windows
$vscodePath = "$env:APPDATA\Code\User"
Copy-Item .\vscode\settings.json "$vscodePath\settings.json"
Copy-Item .\vscode\keybindings.json "$vscodePath\keybindings.json"
```

### MCP

将配置复制到对应 AI IDE 的配置目录即可（具体路径因工具而异）。

## 📌 设计理念

1. **Vim 优先** — 所有编辑器都通过 Vim 模拟层操作，保持统一肌肉记忆
2. **键位一致** — IdeaVim 与 VSCodeVim 使用相同的 Leader 键和核心映射
3. **`Ctrl+N/P` 导航范式** — 在所有上下文中用 `Ctrl+N/P` 做上下选择，取代默认的方向键
4. **中文开发友好** — 自动输入法切换、中文注释偏好、中文 AI 助手
5. **AI 增强** — 集成多个 AI 助手和 MCP 工具链，提升开发效率

## 📄 License

MIT
