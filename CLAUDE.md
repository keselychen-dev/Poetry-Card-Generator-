# CLAUDE.md — Poetry Card Generator

**GitHub 仓库**：https://github.com/keselychen-dev/Poetry-Card-Generator-

## 项目概述

小学生部编版古诗词图文卡片生成器，纯前端单文件应用。收录 101 首部编版古诗，支持 AI 生成诗意插画，导出 PNG 卡片。

## 架构

- **单文件应用**：所有代码在 `index.html` 中（HTML + CSS + JS），无构建步骤
- **古诗数据**：`RAW_POEMS` 数组内嵌在 JS 中，101 首诗按 `[年级Key, 标题, 作者, ...联句]` 格式存储
- **年级映射**：`GRADE_MAP` 将 `"1a"→{grade:"一年级",semester:"上册"}` 等映射
- **句子拆分**：`splitToSentences()` 将联句拆为单句，保留标点符号（`，` `。`）
- **主题检测**：`detectTheme()` 根据诗中关键词匹配春/夏/秋/冬/古典主题
- **意象提取**：`IMG` 数组中英对照，`generatePoemPrompt()` 自动生成英文 AI 绘图 Prompt
- **卡片布局**：标题 + 作者 + 年级 → 诗文 → 插画区 → 诗意赏析，上下分区
- **API 调用**：kie.ai 异步 API（POST createTask → 轮询 GET recordInfo），支持两个模型
- **图片存储**：远程 URL 存 localStorage，base64 仅存内存（防溢出）
- **导出**：html2canvas 3x 缩放导出 PNG

## 关键文件

| 文件 | 说明 |
|------|------|
| `index.html` | 完整应用，唯一需要运行的文件 |
| `prd.md` | 产品需求文档（古诗词卡片 Prompt 生成规则） |
| `小学必备古诗.md` | 101 首古诗原始数据参考 |
| `api-GPT-2.md` / `api-nano banana.md` | kie.ai API 文档 |

## 修改注意事项

- `index.html` 是唯一代码文件，修改都在这里进行
- 修改后用 `node -e "new Function(require('fs').readFileSync('index.html','utf8').match(/<script>([\s\S]*?)<\/script>/)[1])"` 验证 JS 语法
- `POEM_EXPLAIN` 对象中避免使用中文双引号 `""`，用 `「」` 代替（会引发 JS 语法错误）
- 古诗数据在 `RAW_POEMS` 数组中，格式：`["年级Key","标题","作者","联1","联2",...]`
- 新增古诗时需同步更新 `POEM_EXPLAIN` 对象和 `IMG` 意象映射
