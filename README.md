# Poetry Card Generator

> 小学生部编版古诗词图文卡片生成器 — 一键生成精美的古诗学习卡片

一个基于 AI 绘图的单页应用，收录部编版小学语文全部 101 首古诗词，自动匹配春/夏/秋/冬/古典五大主题，支持 AI 生成诗意插画，可导出 PNG 打印卡片。

## 功能特色

- **101 首部编版古诗** — 覆盖一年级到六年级全部古诗词，按年级册次分组
- **AI 智能插画** — 自动分析诗意意象生成英文 Prompt，调用 kie.ai API 生成配图
- **5 套配色主题** — 春/夏/秋/冬/古典，根据诗中关键词自动匹配
- **诗意赏析** — 每首诗配有儿童友好的白话文解读
- **一键导出 PNG** — 高清 3 倍率导出，适合打印
- **手写书法字体** — 马善政楷体 + 站酷小薇，古典与童趣兼具
- **支持手动上传** — 可粘贴或上传本地图片作为插画

## 技术栈

- 纯前端单文件应用（HTML + CSS + JS），无需构建
- [html2canvas](https://github.com/niklasvh/html2canvas) 用于导出图片
- Google Fonts（Ma Shan Zheng、ZCOOL XiaoWei、Noto Serif SC）
- AI 绘图 API：[kie.ai](https://kie.ai)（GPT Image 2 / Nano Banana Pro）

## 快速开始

1. 克隆仓库
   ```bash
   git clone https://github.com/YOUR_USERNAME/poetry-card-generator.git
   cd poetry-card-generator
   ```

2. 用浏览器打开 `index.html` 即可使用

3. 如需 AI 生成插画功能：
   - 访问 [kie.ai/api-key](https://kie.ai/api-key) 获取 API Key
   - 在页面右侧控制面板输入并保存 Key

## 使用方法

1. **选择古诗** — 左侧列表按年级分组，支持搜索诗名、作者、内容
2. **选择主题** — 可手动切换 5 套配色，或使用自动匹配
3. **生成插画** — 编辑自动生成的 Prompt（可选），点击"生成插画"
4. **导出卡片** — 点击"导出卡片 PNG"下载高清图片

## 项目结构

```
poetry-card-generator/
├── index.html          # 完整单页应用（HTML + CSS + JS）
├── prd.md              # 产品需求文档
├── 小学必备古诗.md      # 古诗原始数据
├── api-GPT-2.md        # GPT Image 2 API 文档
├── api-nano banana.md  # Nano Banana Pro API 文档
├── CLAUDE.md           # Claude Code 项目指引
└── README.md           # 本文件
```

## 截图

卡片包含：古诗标题、朝代作者、年级信息、诗文、诗意插画、诗意赏析，整体呈现中国古典水彩绘本风格。

## License

MIT
