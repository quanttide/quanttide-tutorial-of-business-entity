# CHANGELOG

## [0.4.0] - 2026-05-19

### Added

- intro/ 经营现状入门、管理体系、商业模式、战略焦点三篇教程
- human/ 人事教程、离职工作教程
- asset/ 集中治理教程
- stdn/ 标准化教程、章程式工作教程
- 建设企业文化教程
- 量潮课堂经营目标教程
- 个人所得税退税教程
- 机制设计评估教程
- 拒绝越级沟通教程

### Changed

- asset/index.md 重命名为 asset/batch-maintain.md
- 越级沟通教程重构，聚焦第二类绕过者
- 离职教程重写为叙事风格
- 更新 myst.yml 目录结构

### Removed

- 移除多余的 external.md

## [0.3.0] - 2026-05-12

### Added

- AGENTS.md，记录目录排序规则（业务 → 管理类职能 → 工程类职能）
- 开源协议选择策略（share/license.md），以叙事风格阐述 CC-BY 与 Apache 2.0 选型逻辑
- qtdata/ 注册到 myst.yml TOC（量潮数据章节）

### Changed

- myst.yml TOC 重排：量潮数据移至最前，职能章节按管理→工程排序
- share/license.md 重写为首人称叙事风格
- 补充 BSD、LGPL 排除说明

## [0.2.2] - 2026-05-12

### Added

- qtdata/ 目录（customer.md, index.md, project.md）
- 项目管理文档：协作效率、事前沟通、客户延迟应对

### Changed

- 完善 qtdata/index.md 量潮数据经营现状总结

## [0.2.1] - 2026-05-11

### Added

- DevOps 章节：语义化版本发布规范（sematric_version.md）
- myst.yml 目录注册 sematric_version.md

## [0.2.0] - 2026-05-11

### Added

- myst.yml 项目配置（目录结构、作者、许可证、站点模板）
- index.md 入口页面
- 部署工作流：GitHub Actions 自动构建并部署 MyST 静态站点到 GitHub Pages
- .gitignore 忽略 _build/ 构建产物
- 写作规范章节：write/index.md《如何快速撰写高质量的工作文章？》、write/bylaw.md《如何快速撰写高质量的工作章程？》

### Changed

- GitHub Pages 部署命令从 `myst build --site` 修复为 `myst build --html`
- 目录结构调整：写作章节重命名并调整顺序

## [0.1.0] - 2026-05-05

### Added

- ROADMAP.md 产品路线图
- company-representative.md 法定代表人制度文档

### Changed

- definitions.md 从 appendix/ 移至 intro/

## [0.0.2] - 2026-04-30

### Added
- 添加教程入口索引 (index.md)
- 添加定义文件 (definitions.md)
- 添加 BRD 机制设计洞见
- 添加哲学教程
- 添加 CONTRIBUTING 文件

### Changed
- 重构 vibe_writing 目录结构，移至 generative_ai 同级
- 根据 GLM 评审意见重构 Vibe Writing 文档
- 更新 CONTRIBUTING 适配主仓库
- 移除/减少文档粗体使用，应用 docs-format 格式规范

### Removed
- 将哲学内容提取至独立仓库

## [0.0.1] - 2026-04-05

### Added
- 添加教程简介和写作规范文档
- 添加 Markdown 最佳实践指南
- 添加管理教程（asset_management）
- 添加 Git submodule 拉取指南
- 添加 LLM 命令行工具使用指南
- 添加 LLM 常见问题（Key 输入失败、代理崩溃、模型识别、配置路径）
- 添加 Vibe Writing 多模型协作写作工作流

### Changed
- 重构生成式 AI 文档结构，将 README.md 移至 cli/llm.md 并新增 index.md
- 重构 vibe_writing 目录结构，移至根目录
- 根据 GLM-5 评审意见重构 LLM 使用指南
- 优化管理教程内容

### Removed
- 删除过时的文件
- 移除 Markdown 最佳实践指南
- 移除对话归属标记
- 移除多余的分割线
