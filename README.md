# claude-design-style

将 Anthropic / Claude 官网的设计美学应用到任意 Web 项目。基于对 anthropic.com、claude.ai 和 Claude App 界面的深度分析提炼。

这套设计系统强调**温暖简约**、**排版清晰**、**充裕留白**和**文学阅读体验**。

---

## 安装

### 方式一：使用 clawhub（推荐）

```bash
clawhub install claude-design-style
```

### 方式二：手动安装

将本仓库克隆到 Claude Code 的技能目录：

```bash
git clone https://github.com/xdesign678/claude-design-style.git \
  ~/.claude/skills/claude-design-style
```

验证安装：

```bash
ls ~/.claude/skills/claude-design-style/SKILL.md
```

---

## 使用方法

安装后，在与 Claude Code 对话时，使用以下任意触发词即可激活该技能：

### 中文触发词

- "做成 Claude 风格"
- "温暖简约设计"
- "文学感网页"
- "Anthropic 设计风格"
- "阅读体验"
- "克制优雅设计"

### 英文触发词

- "Claude style"
- "Anthropic design"
- "elegant reading design"
- "warm minimal design"
- "literary web design"

### 示例对话

```
用户：帮我把这个页面做成 Claude 风格

用户：用 Anthropic 设计风格重新设计这个组件

用户：这个博客页面改成温暖简约设计，有文学阅读感
```

---

## 适用场景

| 场景 | 推荐 |
|------|------|
| 博客、文章页面 | ✅ 首选 |
| 知识库、文档站 | ✅ 首选 |
| AI 对话界面 | ✅ 适合 |
| 作品集、个人主页 | ✅ 适合 |
| 数据大盘 / Dashboard | ❌ 不适合 |
| 电商、营销落地页 | ❌ 不适合 |
| 游戏 / 娱乐界面 | ❌ 不适合 |

---

## 设计系统概览

### 核心色板

| Token | 值 | 用途 |
|-------|-----|------|
| `--bg-primary` | `#faf9f5` | 温暖奶油色背景 |
| `--text-primary` | `#141413` | 标题与正文 |
| `--text-secondary` | `#5e5d59` | 辅助文字 |
| `--bg-button` | `#0f0f0e` | 主按钮背景 |
| `--brand-clay` | `#d97757` | Claude 品牌橙（仅 Logo） |

### 字体系统

| 用途 | 字体栈 |
|------|--------|
| 正文阅读 | `Lora, "Noto Serif SC", Georgia, serif` |
| 标题 / UI | `Geist, Inter, system-ui, sans-serif` |
| 代码 | `"Geist Mono", "JetBrains Mono", monospace` |

### 关键规则

- 按钮圆角：`7.5px`（Anthropic 标志性圆角，非 pill 形）
- 内容最大宽度：640px（阅读）/ 768-840px（应用）
- 无渐变，无纹理，无重阴影
- 行高 1.6（正文），1.1-1.3（标题）
- 过渡动画 150-300ms ease

---

## 参考文件

技能包含 10 个按需加载的参考文件，Claude 会根据任务类型自动选择加载：

| 文件 | 内容 |
|------|------|
| `references/colors.md` | 完整色彩 Token、Tailwind 配置 |
| `references/typography.md` | 字体加载、类型比例、Tailwind 配置 |
| `references/components.md` | 代码块、下拉、弹窗、徽章、表格等 |
| `references/layout.md` | 网格系统、响应式断点、页面模板 |
| `references/motion.md` | 关键帧、过渡、加载状态、滚动行为 |
| `references/brand.md` | Logo SVG、图标规范、品牌使用规则 |
| `references/claude-app.md` | AI 对话 UI：消息气泡、输入框、侧边栏 |
| `references/forms.md` | 表单验证状态、字段组、特殊输入控件 |
| `references/states.md` | 空状态、骨架屏、Toast、错误页 |
| `references/shadcn.md` | shadcn/ui 主题配置、HSL 变量、globals.css |

---

## 不适合此技能的情况

- 通用的"让它更好看"请求（无明确审美方向）
- 需要高信息密度的数据展示界面
- 需要强调品牌个性的营销页面

---

## License

详见 [LICENSE.txt](LICENSE.txt)
