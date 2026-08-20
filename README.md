# papers-dataset

科研文献综述语料库：**arXiv AI/ML/LLM/Agent 方向论文元数据 + PDF 全文**。

由 Paperimage 项目的 `experiments/literature_review` 爬取导出（2026-08-20 生成）。

## 数据集概况

| 项目 | 数值 |
| --- | --- |
| 论文总数（元数据） | 1000 篇 |
| 已下载 PDF | 996 篇（4 篇下载失败） |
| 年份分布 | 2023: 90 篇，2024: 276 篇，2025: 634 篇 |
| 主要分类 | cs.AI (296), cs.CL (264), cs.MA (213), cs.LG (78) |
| 数据来源 | arXiv API + OpenAlex |
| 总量 | 约 2.9 GB |

检索式：

```
(cat:cs.AI OR cat:cs.LG OR cat:cs.CL OR cat:cs.MA)
AND (all:"agent" OR all:"multi-agent" OR all:"LLM" OR all:"large language model")
AND submittedDate:[202301010000 TO 202512312359]
```

## 目录结构

```
papers-dataset/
├── papers.json        # 1000 条论文元数据（标题、摘要、作者、DOI、引用数等）
├── papers.csv         # 同上的 CSV 版本
├── index.md           # 索引
├── _meta.json         # 抓取配置与统计（年份/分类/PDF 下载结果）
├── _raw/
│   ├── arxiv_metadata.json    # arXiv API 原始元数据
│   ├── papers_enriched.json   # 经 OpenAlex 富化后的元数据
│   └── pdf_progress.json      # PDF 下载进度记录
└── pdf/               # 996 篇论文 PDF，文件名 = arXiv ID（如 2508.17188.pdf）
```

## 使用

```powershell
# 按 arXiv ID 查找
Get-ChildItem pdf -Filter "*.pdf" | Where-Object { $_.BaseName -eq "2508.17188" }
```

## 许可声明

- PDF 内容版权归各论文原作者/出版商所有，本仓库仅做研究语料存档与分发。
- 元数据（标题/摘要/DOI 等）来自 arXiv 与 OpenAlex 公共 API，按各自条款使用。
- 请勿用于任何侵犯原作者权利的用途。
