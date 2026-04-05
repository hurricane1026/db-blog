# db-blog

一个以数据库技术为主题的博客仓库，当前先收录一组关于云数据库的中文系列文章。

站点使用 Hugo + PaperMod 构建，内容目录采用 Hugo 默认的 `content/` 结构，并按“栏目 / 专题 / 文章”方式组织内容。

## 目录

- 云数据库系列
- [云数据库系列总览](./content/series/cloud-database/00-series-overview.md)
- [第 1 篇：云数据库到底改变了什么](./content/series/cloud-database/01-what-cloud-database-changed.md)
- [第 2 篇：关系型、NoSQL、NewSQL 怎么选](./content/series/cloud-database/02-how-to-choose.md)
- [第 3 篇：高可用、备份与容灾的真实成本](./content/series/cloud-database/03-ha-backup-and-dr.md)
- [第 4 篇：性能治理不是只看 CPU](./content/series/cloud-database/04-performance-governance.md)
- [第 5 篇：云数据库为什么总是“越用越贵”](./content/series/cloud-database/05-cost-control.md)
- [第 6 篇：从自建 MySQL 迁移到云数据库的实战路径](./content/series/cloud-database/06-migration-playbook.md)

- Lakehouse 系列
- [Lakehouse 系列总览](./content/series/lakehouse/00-series-overview.md)
- [第 1 篇：Lakehouse 到底在解决什么问题](./content/series/lakehouse/01-what-lakehouse-solves.md)
- [第 2 篇：Iceberg、Delta Lake、Hudi 该怎么看](./content/series/lakehouse/02-table-format-selection.md)
- [第 3 篇：Lakehouse 的数据摄入和建模别只盯着批流一体](./content/series/lakehouse/03-ingestion-and-modeling.md)
- [第 4 篇：Lakehouse 成本问题往往不在存储](./content/series/lakehouse/04-compute-and-cost.md)
- [第 5 篇：Lakehouse 真正上线，卡在治理而不是查询引擎](./content/series/lakehouse/05-governance-and-production.md)

## 说明

当前文章已经补齐 Hugo 可用的 Front Matter，并提供了根目录 `hugo.toml` 配置，可直接作为 Hugo 站点内容渲染。

## 内容结构

- `content/_index.md`: 首页内容
- `content/series/_index.md`: 专题栏目页
- `content/series/cloud-database/`: 云数据库专题及文章
- `content/articles/_index.md`: 全部文章页
- `content/tags/_index.md`: 标签页说明
- `content/categories/_index.md`: 分类页说明

## 本地开发

启动本地开发服务器：

```bash
hugo server -D
```

构建生产静态文件：

```bash
hugo --minify
```

## 新增文章流程

1. 先确定文章属于哪个专题；如果是新专题，先在 `content/series/` 下建新的专题目录和 `_index.md`。
2. 使用 archetype 生成草稿：

```bash
hugo new series/<topic>/<slug>.md
```

3. 补齐 Front Matter：
   - `summary`
   - `description`
   - `keywords`
   - `categories`
   - `tags`
   - `series`
   - `weight`
   - `cover.image`
4. 如果希望保持固定访问路径，显式填写 `url`。
5. 为文章准备一张封面图，放到 `static/covers/` 下，并在卡片页和文章页复用。

可以参考 [archetypes/article.md](./archetypes/article.md) 作为基础模板。

## 页面组织

- 首页 `/`: 主题边界、推荐阅读、专题文章
- 专题栏目 `/series/`: 所有专题入口
- 全部文章 `/articles/`: 全站文章聚合
- 专题页 `/cloud-database-series/`: 单个专题的阅读入口
- 标签 `/tags/` 与分类 `/categories/`: 从问题域和关键词切入

## 部署

仓库已提供 GitHub Pages 工作流：

- [`.github/workflows/hugo.yml`](./.github/workflows/hugo.yml)

默认在 `main` 分支 push 后构建并发布到 GitHub Pages。部署前请确认：

1. GitHub Pages 已启用，并选择 “GitHub Actions” 作为来源。
2. 仓库设置允许 Actions 使用 `pages` 和 `id-token` 权限。
3. `baseURL` 与实际站点域名一致。
4. 生产机如果直接 `git pull` 后构建，需要先确保 SSH key 能访问 GitHub，再执行 `git submodule update --init --recursive` 拉取 `themes/PaperMod`。

当前 `.gitmodules` 已切到 SSH 地址，便于无法通过 HTTPS 拉取子模块的服务器部署；GitHub Actions 会在 CI 中临时改回 HTTPS 再初始化子模块。
