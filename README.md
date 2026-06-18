# Clone Website

[English](./README.en.md) | 中文

> 一个技术栈自由选择、AI 代理自由选择的网站克隆 Skill —— 将任意网站像素级还原为干净的现代代码库

## 特性

- **🔧 技术栈自由选择** —— 不强制使用 React/Next.js，你可以任意指定框架、CSS 方案、构建工具（React、Vue、Svelte、Tailwind、Vite 等皆可）
- **🤖 代理无关** —— 不绑定特定 AI 编码代理，支持 Claude Code、Codex、Cursor、Windsurf、Cline、Trae 等
- **🎯 像素级还原** —— 通过 `getComputedStyle()` 提取精确 CSS 值，而非估算
- **🎭 多状态提取** —— 捕获元素的默认状态、悬停状态、滚动状态、点击状态等所有视觉状态
- **🧩 组件化构建** —— 按区块拆分，每个组件都有详细的规格文件作为构建契约
- **📱 响应式适配** —— 在桌面（1440px）、平板（768px）、移动端（390px）三种视口下提取
- **🎬 行为还原** —— 不仅提取静态样式，还提取滚动动画、悬停效果、标签切换等交互行为
- **📦 真实资源** —— 下载真实的图片、视频、SVG、字体，而非使用占位符
- **✅ 可验证构建** —— 每个组件构建后都验证编译通过，最终全项目构建必须成功

## 支持的 AI 编码代理

本 Skill 遵循标准的 Skill 规范（`SKILL.md` + YAML frontmatter），可安装在任何支持 Skill 机制的 AI 编码代理上：

| 代理 | Skill 目录 | 状态 |
|---|---|---|
| [Claude Code](https://docs.anthropic.com/en/docs/claude-code) | `~/.claude/skills/` 或 `.claude/skills/` | 推荐 |
| [Codex CLI](https://github.com/openai/codex) | `.codex/skills/` | 支持 |
| [Cursor](https://cursor.com/) | `.cursor/`（通过 rules） | 支持 |
| [Windsurf](https://codeium.com/windsurf) | `.windsurf/workflows/` | 支持 |
| [Cline](https://github.com/cline/cline) | `.cline/` | 支持 |
| [Trae](https://trae.cn/) | `.trae/skills/` | 支持 |
| [OpenCode](https://opencode.ai/) | `.opencode/commands/` | 支持 |
| [Gemini CLI](https://github.com/google-gemini/gemini-cli) | `.gemini/commands/` | 支持 |
| [GitHub Copilot](https://github.com/features/copilot) | `.github/`（通过 instructions） | 支持 |
| [Amazon Q](https://aws.amazon.com/q/developer/) | `.amazonq/` | 支持 |
| [Augment Code](https://www.augmentcode.com/) | `.augment/commands/` | 支持 |
| [Aider](https://aider.chat/) | `.aider.conf.yml` | 支持 |
| [Continue](https://continue.dev/) | `.continue/` | 支持 |
| [Roo Code](https://github.com/RooCodeInc/Roo-Code) | `.roo/` | 支持 |

> **注意**：不同代理的 Skill 加载机制略有差异，安装时请参考你所使用代理的官方文档。本仓库采用 **flat layout**（`SKILL.md` 在仓库根目录），这是最通用的结构。

## 安装

### 方式一：Git Clone（推荐）

将本仓库直接克隆到你所使用的 AI 编码代理的 Skill 目录下：

```bash
# Claude Code（全局安装）
git clone https://github.com/huangmingfu/clone-website.git ~/.claude/skills/clone-website

# Claude Code（项目级安装）
git clone https://github.com/huangmingfu/clone-website.git .claude/skills/clone-website

# Codex CLI
git clone https://github.com/huangmingfu/clone-website.git .codex/skills/clone-website

# Trae
git clone https://github.com/huangmingfu/clone-website.git .trae/skills/clone-website
```

其他代理请参考上表中的 Skill 目录路径，将仓库克隆到对应位置即可。

### 方式二：使用 skillz 包管理器（Claude Code）

如果你使用 [skillz](https://github.com/jakegoldsborough/skillz)（Claude Code 的 Skill 包管理器）：

```bash
skillz install github:huangmingfu/clone-website
```

### 方式三：手动下载

下载 `SKILL.md` 文件，放置到你所使用的 AI 编码代理的 Skill 目录下，并命名为 `clone-website/SKILL.md`。

## 使用方法

在你的 AI 编码代理中，输入以下命令调用 Skill：

```
/clone-website <目标网站URL>
```

例如：
```
/clone-website https://example.com
```

也可以同时克隆多个网站：
```
/clone-website https://example.com https://another-site.com
```

### 使用示例

你可以在命令中直接指定想要使用的技术栈和输出目录，Skill 会按你的要求构建：

```
/clone-website 使用vue3最新技术栈全家桶，克隆 https://www.deepseek.com 到根目录的 demo 文件夹下面
```

上面的命令会：
- 使用 **Vue 3 全家桶**（Vue 3 + Vue Router + Pinia + Vite 等）作为技术栈
- 克隆 `https://www.deepseek.com` 的页面
- 将项目代码输出到当前项目根目录下的 `demo/` 文件夹中

更多用法示例：

```
# 使用 React + Next.js + Tailwind CSS 克隆
/clone-website 使用 Next.js + Tailwind CSS 克隆 https://example.com 到 ./my-clone

# 使用原生 HTML/CSS/JS 克隆（无框架）
/clone-website 使用原生 HTML+CSS+JS 克隆 https://example.com

# 使用 Svelte + Vite 克隆到指定目录
/clone-website 使用 Svelte + Vite 克隆 https://example.com 到 ./sites/example-clone
```

> **说明**：不同代理调用 Skill 的方式可能略有差异。大多数代理支持 `/skill-name` 语法，部分代理可能通过自然语言描述触发（例如"帮我克隆这个网站 https://example.com"）。如果你没有在命令中指定技术栈，Skill 会在开始前询问你偏好的技术栈（框架、CSS 方案、构建工具），请根据你的需求选择。

## 工作流程

Skill 执行一个五阶段流水线：

### Phase 1: 侦察（Reconnaissance）
- 全页面截图（桌面 1440px + 移动端 390px）
- 全局提取：字体、颜色、favicon、全局 UI 模式
- 强制交互扫描：滚动扫描、点击扫描、悬停扫描、响应式扫描
- 页面拓扑映射：记录每个区块的顺序、布局、交互模型

### Phase 2: 基础构建（Foundation Build）
- 更新字体配置
- 更新全局样式（颜色 token、间距、关键帧动画、全局滚动行为）
- 创建类型定义（如使用 TypeScript）
- 提取 SVG 图标为命名组件
- 下载全局资产（图片、视频、字体）
- 验证项目构建成功

### Phase 3: 组件规格与构建（Component Specification and Build）
对每个区块执行三步循环：
1. **提取** —— 截图、提取 CSS、提取多状态样式、提取真实内容、识别资产、评估复杂度
2. **写规格文件** —— 在 `docs/research/components/` 下创建详细的组件规格文件
3. **构建组件** —— 根据规格文件构建组件，验证编译通过

### Phase 4: 页面组装（Page Assembly）
- 导入所有区块组件
- 实现页面级布局（滚动容器、列结构、sticky 定位、z-index 分层）
- 连接真实内容到组件 props
- 实现页面级行为（滚动吸附、滚动驱动动画、IntersectionObserver 等）
- 验证全项目构建通过

### Phase 5: 视觉 QA 对比（Visual QA Diff）
- 并排对比截图（原站 vs 克隆）
- 桌面端和移动端分别对比
- 测试所有交互行为
- 修复发现的差异

## 技术栈自由选择

本 Skill **允许你自由选择任何技术栈**，不强制使用任何特定框架或工具。在 Pre-Flight 阶段，Skill 会询问你偏好的技术栈（如果你在命令中已经指定，则按你的指定执行）：

| 类别 | 可选项（不限于） |
|---|---|
| **框架** | React、Vue、Svelte、Solid、Astro、vanilla HTML、Angular、Preact、Lit、Qwik... |
| **CSS 方案** | Tailwind CSS、UnoCSS、CSS Modules、styled-components、vanilla CSS、Sass、Less、Emotion、Panda CSS... |
| **构建工具** | Vite、Next.js、Nuxt、SvelteKit、webpack、Rollup、esbuild、Parcel、Astro、TanStack Start... |

你也可以选择 **vanilla HTML + CSS + JavaScript**（无框架），Skill 同样支持。

**关键原则**：技术栈完全由你决定，Skill 不假设、不推荐、不默认任何特定技术栈。

## 前置条件

- [Node.js](https://nodejs.org/) 18+（用于运行资产下载脚本）
- 一个支持 Skill 机制的 AI 编码代理（见[支持的 AI 编码代理](#支持的-ai-编码代理)）
- 浏览器自动化 MCP 工具（如 Chrome DevTools MCP、Playwright MCP、browser-use 等）

## 使用案例

- **平台迁移** —— 将你拥有的网站从 WordPress/Webflow/Squarespace 迁移到现代代码库
- **源码找回** —— 你的网站还在线上但代码库丢失了，用现代格式找回代码
- **学习研究** —— 通过与真实代码协作，解构生产级网站如何实现特定的布局、动画和响应式行为
- **设计还原** —— 将设计稿或参考网站还原为可运行的代码

## 注意事项 / 免责声明

### ✅ 鼓励的用途
- 克隆你自己的网站用于迁移或备份
- 学习研究生产级网站的实现技巧
- 将设计参考还原为代码用于学习

### ❌ 禁止的用途
- **钓鱼或冒充** —— 不得用于欺骗性目的、冒充他人或任何违法活动
- **盗用他人设计** —— logo、品牌资产、原创文案归其所有者所有
- **违反服务条款** —— 部分网站明确禁止抓取或复制，使用前请先检查

使用者自行承担因使用本工具产生的所有法律责任。

## 项目结构

```
clone-website/                # 本仓库（flat layout）
├── SKILL.md                  # Skill 定义文件（必需）
├── README.md                 # 中文 README（默认）
├── README.en.md              # 英文 README
├── LICENSE                   # MIT 许可证
└── .gitignore
```

## 参考项目

本 Skill 在设计过程中参考了以下开源项目的工作流程与思路：

- **[firecrawl/open-lovable](https://github.com/firecrawl/open-lovable)** —— 由 Firecrawl 团队开发的 AI 构建 React 应用示例，启发了"通过 AI 代理驱动网站还原"的整体思路。
- **[JCodesMore/ai-website-cloner-template](https://github.com/JCodesMore/ai-website-cloner-template)** —— 一个基于 Next.js 的网站克隆模板项目，其五阶段流水线（侦察、基础构建、组件规格、并行构建、组装 QA）和组件规格文件作为构建契约的设计对本 Skill 有重要启发。

与这两个项目不同的是，本 Skill **允许自由选择任何技术栈**（不绑定 React/Next.js）且**代理无关**（不绑定特定 AI 编码代理），开发者可自由选择任何框架、CSS 方案、构建工具和 AI 编码代理。

## 许可证

[MIT](./LICENSE)
