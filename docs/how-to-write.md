---
title: 文档库使用说明
summary: 怎么写、怎么发布、改完多久生效
date: 2026-11-06
tags: [说明]
order: 1
---

# 文档库使用说明

这份文档本身就是示例，可以直接改。

## 发布流程

1. 本地编辑 `docs/` 下的 `.md` 文件
2. 提交并推送到本仓库
3. 等待约 5 分钟，站点自动同步

**不需要重新部署站点。** 站点在运行时拉取本仓库的内容，改文档和改站点代码是两件事。

## frontmatter 字段

| 字段 | 说明 | 缺省行为 |
| --- | --- | --- |
| `title` | 展示标题 | 取正文第一个 H1，再退化为文件名 |
| `summary` | 列表页摘要 | 不显示摘要行 |
| `date` | 日期 | 不显示日期 |
| `tags` | 标签，用于筛选 | 标量或数组均可 |
| `order` | 排序权重，越小越靠前 | 排在最后 |

## 支持的 Markdown 语法

标题、列表、表格、引用、代码块、行内代码、链接、加粗、删除线。

代码块会做语法高亮，支持的语言：

`bash` `css` `diff` `dockerfile` `go` `ini` `javascript` `json` `markdown` `python` `rust` `scss` `shell` `sql` `typescript` `xml` `yaml`

```typescript
interface DocMeta {
  slug: string;
  title: string;
  tags: string[];
}
```

## 安全约束

文档里**不能写内嵌 HTML**。站点渲染时会把 `<script>`、`<img onerror=...>` 这类内容转义成纯文本，防止脚本注入。

链接只支持三种形式：

```markdown
[正常外链](https://example.com)
[站内路径](/docs/other-doc)
[邮件](mailto:someone@example.com)
```

`javascript:` 这类协议的链接会被自动剥掉 href。
