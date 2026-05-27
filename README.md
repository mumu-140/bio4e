# Bioinformatics 4e · 中英双语翻译

《Bioinformatics》(4th Edition) 中英双语翻译站。覆盖全 18 章，提供三种阅读形态：

- **连续阅读版** — 单页全书，含全文搜索与折叠章节
- **双语 Wiki** — 每章一页，英文原文与中文译文对照
- **术语表** — 全书核心术语对照

纯静态站点，无构建步骤，任意 HTTP 服务器或 GitHub Pages 即可托管。

## 在线访问

GitHub Pages 部署后默认地址：

```
https://mumu-140.github.io/bio4e/
```

仓库：<https://github.com/mumu-140/bio4e>

## 入口

| 页面 | 路径 | 说明 |
| --- | --- | --- |
| 索引页 | `index.html` | 章节卡片导航 + 实时搜索 |
| 连续阅读 | `bio4e/book.html` | 单页全书 6.1 MB，含搜索高亮 |
| 双语 Wiki | `bio4e/wiki/index.html` | 18 章独立页面 |
| 术语表 | `bioinformatics_glossary.html` | 中英对照术语表 |

## 本地预览

仓库根目录用 Python 起一个静态服务即可，无需任何依赖：

```bash
cd bio4e            # 仓库根目录
python3 -m http.server 8000
# 浏览器访问 http://localhost:8000/
```

任意其他静态服务也可：

```bash
npx serve .              # Node
caddy file-server -listen :8000  # Caddy
```

> 直接双击 `index.html` 用 `file://` 协议也能看到大多数内容，但 `book.html?q=...` 等基于 query string 的搜索跳转，建议走 HTTP。

## 部署到 GitHub Pages

仓库已经在 `main` 分支，启用 Pages 即可：

1. GitHub 仓库 → **Settings → Pages**
2. **Source** 选 `Deploy from a branch`
3. **Branch** 选 `main` / `/ (root)`，保存
4. 等待 1–2 分钟，访问 `https://<user>.github.io/bio4e/`

更新流程：本地改完 → `git commit && git push origin main`，Pages 自动重新发布。

## 目录结构

```
.
├── index.html                       # 索引页（章节卡片 + 搜索）
├── bioinformatics_glossary.html     # 术语表
└── bio4e/
    ├── book.html                    # 连续阅读版（单页全书）
    ├── wiki/
    │   ├── index.html               # Wiki 总入口
    │   └── ch01.html … ch18.html    # 18 章双语页
    └── <NN>_<Chapter_Name>/         # 各章 PDF 渲染图与原稿素材
```

## 使用提示

- **搜索**：索引页与连续阅读版的导航栏都有搜索框。输入后实时下拉显示匹配章节，点击跳转；回车进入连续阅读版并高亮关键词。
- **锚点跳转**：每章在 `book.html` 中有稳定锚点，如 `book.html#ch3-assessing-pairwise-sequence-similarity-blast-and-fasta`，可直接引用。
- **导出**：连续阅读版顶部「导出本章」按钮可导出当前章节内容。
- **折叠**：章节默认折叠以加快加载，点击章节标题展开/收起。

## 维护

- 翻译内容直接编辑对应 HTML 文件；目录与章节命名保持现状。
- 资源体积较大（合并约 18 MB），避免在 commit message 之外再引入构建产物或缓存目录。`.gitignore` 已排除 `.DS_Store` 与 macOS 元数据。
- 最近一次内容更新日期在 `index.html` 底部维护。

---

# Bioinformatics 4e · Bilingual Translation

A bilingual (English + Simplified Chinese) translation site for *Bioinformatics* (4th Edition). All 18 chapters are available in three reading modes:

- **Single-page book** — full text on one page with in-page search and collapsible sections
- **Bilingual wiki** — one page per chapter, English original alongside the Chinese translation
- **Glossary** — a parallel English–Chinese glossary of key terms

Pure static HTML. No build step. Serve it with any HTTP server or GitHub Pages.

## Live site

Default GitHub Pages URL after deployment:

```
https://mumu-140.github.io/bio4e/
```

Repository: <https://github.com/mumu-140/bio4e>

## Entry points

| Page | Path | Notes |
| --- | --- | --- |
| Home | `index.html` | Chapter cards + live search |
| Continuous reader | `bio4e/book.html` | 6.1 MB single page, search with highlight |
| Bilingual wiki | `bio4e/wiki/index.html` | 18 standalone chapter pages |
| Glossary | `bioinformatics_glossary.html` | English–Chinese term table |

## Run locally

From the repo root, start any static file server:

```bash
cd bio4e
python3 -m http.server 8000
# open http://localhost:8000/
```

Other options:

```bash
npx serve .
caddy file-server -listen :8000
```

> Opening `index.html` directly via `file://` mostly works, but query-string search (`book.html?q=...`) is more reliable over HTTP.

## Deploy on GitHub Pages

The repo already lives on `main`. To publish:

1. GitHub repo → **Settings → Pages**
2. **Source**: `Deploy from a branch`
3. **Branch**: `main` / `/ (root)`, save
4. Wait 1–2 minutes, then visit `https://<user>.github.io/bio4e/`

To update: commit and push to `main`; Pages will rebuild automatically.

## Project layout

```
.
├── index.html                       # Home (chapter cards + search)
├── bioinformatics_glossary.html     # Glossary
└── bio4e/
    ├── book.html                    # Continuous reader (full book)
    ├── wiki/
    │   ├── index.html               # Wiki landing
    │   └── ch01.html … ch18.html    # 18 bilingual chapter pages
    └── <NN>_<Chapter_Name>/         # Per-chapter rendered PDF figures
```

## Usage tips

- **Search**: both the home page and the continuous reader expose a search box. Typing shows a dropdown of matching chapters and lets you click straight to a section; pressing Enter jumps to the continuous reader with query highlighting.
- **Anchors**: each chapter has a stable anchor in `book.html`, e.g. `book.html#ch3-assessing-pairwise-sequence-similarity-blast-and-fasta`.
- **Export**: the "导出本章" button in the continuous reader exports the current chapter.
- **Collapse**: chapters are collapsed by default for faster loading — click a section header to expand.

## Maintenance

- Edit the HTML files directly when updating translations. Keep the chapter directory and file naming as-is.
- Assets are large (~18 MB total). Avoid committing build artefacts or caches; `.gitignore` already excludes `.DS_Store` and macOS metadata.
- The "Last updated" date at the bottom of `index.html` is the source of truth.
