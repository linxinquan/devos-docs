# devos-docs

个人技术文档与学习笔记 —— [developer-os](https://github.com/linxinquan/portfolio) 作品集的文档库。

内容自动同步到站点 `/docs`：站点在运行时拉取本仓库，**改文档只需提交到这里，不需要重新部署站点**（约 5 分钟内生效）。

## 目录

```
docs/
├─ xxx.md
└─ ...
```

文档文件名即站点 URL 片段：`docs/renderer-layer.md` → `/docs/renderer-layer`。

## 写作格式

每个文档是标准 Markdown，文件顶部可选 frontmatter：

```markdown
---
title: Three.js 渲染分层实践
summary: 从场景搭建到资源回收的职责划分
date: 2026-10-30
tags: [Three.js, 性能]
order: 10
---

正文从这里开始。
```

| 字段 | 说明 | 缺省行为 |
| --- | --- | --- |
| `title` | 展示标题 | 取正文第一个 H1，再退化为文件名 |
| `summary` | 列表页摘要 | 不显示摘要行 |
| `date` | 日期 | 不显示日期 |
| `tags` | 标签，用于筛选 | 标量或数组均可，无标签则不显示 |
| `order` | 排序权重，越小越靠前 | 排在最后，同权重按标题排序 |
| `draft` | 标记为草稿 | 公开仓库里仍会展示；隐藏靠私密仓库 |

## 提交

```bash
git clone https://github.com/linxinquan/devos-docs.git
cd devos-docs
# 编辑 docs/ 下的文件
git commit -am "更新文档"
git push
```

## 约定

- 仓库公开，等同于内容公开
- 文档内禁止内嵌 HTML（站点渲染时会转义），链接只支持 http/https/mailto 与相对路径
- 未定稿的内容放私有仓库 `devos-drafts`，站点上需口令解锁才可见
