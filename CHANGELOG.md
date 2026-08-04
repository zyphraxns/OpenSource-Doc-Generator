# 变更日志 | Changelog

本项目所有重要变更均会记录在此文件中。 | All notable changes to this project will be documented in this file.

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，
版本管理遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

Format based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
versioning follows [Semantic Versioning](https://semver.org/).

## [Unreleased]

## [1.2.0] - 2026-08-04

### Changed | 变更

- **仓库结构重组** | **Repository restructure**: 删除 `V2/` 目录，将 V2 版本的 `SKILL.md` 和 `references/` 移至仓库根目录，以便被 skills.sh 等平台检索收录 | Removed `V2/` directory, moved V2 `SKILL.md` and `references/` to the repository root for better discoverability on platforms like skills.sh
- **CHANGELOG 改为中英双语** | **CHANGELOG now bilingual**: 在同一文件中同时提供中文和英文内容 | Now provides both Chinese and English content in a single file

### Added | 新增

- 英文版 SKILL.md（`SKILL.en.md`）| English version of SKILL.md (`SKILL.en.md`)
- 英文版 file-types-guide.md（`references/file-types-guide.en.md`）| English version of file-types-guide.md (`references/file-types-guide.en.md`)
- 英文版 README（`README.en.md`）| English README (`README.en.md`)
- 中文 README 添加英文版链接 | Chinese README now links to the English version

## [1.1.0] - 2026-08-04

### Added | 新增

- 新增第三步「用户确认与选择」交互步骤，在生成文件前向用户展示： | Added Step 3 "User Confirmation & Selection" interaction step, presenting before file generation:
  - 项目分析摘要（让用户确认 AI 理解是否正确）| Project analysis summary (for user to verify AI's understanding)
  - 3-4 个分级推荐方案（全套/标准/基础/最小），每个方案包含文件清单和说明 | 3-4 tiered recommendation plans (Full/Standard/Basic/Minimal), each with file list and description
  - 需要用户确认的问题（许可证类型、文档语言、作者信息等）| Questions requiring user confirmation (license type, document language, author info, etc.)
- 新增「分级推荐方案设计指南」，明确各方案应包含的文件范围 | Added "Tiered Recommendation Plan Design Guide" defining file scope for each plan
- 决策矩阵新增「项目特征 → 方案一/方案二额外包含」对照表 | Decision matrix now includes "Project characteristics → Plan 1/Plan 2 additional files" mapping
- 质量检查清单新增三项检查（许可证类型一致性、文档语言一致性、已有文件不被覆盖）| Quality checklist adds three new checks (license type consistency, document language consistency, existing files not overwritten)

### Changed | 变更

- 工作流程从 4 步扩展为 5 步：项目分析 → 智能推荐分级 → 用户确认与选择 → 文档生成 → 总结报告 | Workflow expanded from 4 to 5 steps: Project Analysis → Intelligent Tiered Recommendations → User Confirmation & Selection → Document Generation → Summary Report
- 核心思路更新为"先分析项目，再智能推荐分级方案，经用户确认后逐一生成" | Core philosophy updated to "Analyze the project first, then present tiered recommendation plans, and generate only after user confirmation"
- 决策矩阵说明更新为"内部参考，最终创建哪些文件由用户决定" | Decision matrix description updated to "internal reference, final file selection decided by user"
- 输出格式从 3 项扩展为 5 项 | Output format expanded from 3 to 5 items

### Reorganized | 重组

- 将 V1 版本文件移入 `V1/` 目录 | Moved V1 files into `V1/` directory
- V2 版本文件放入 `V2/` 目录 | V2 files placed in `V2/` directory
- 根目录保留项目级文档（README、LICENSE、CONTRIBUTING 等）| Root directory retains project-level docs (README, LICENSE, CONTRIBUTING, etc.)

## [1.0.0] - 2026-08-03

### Added | 新增

- 初始发布 | Initial release
- 实现项目分析功能：自动扫描项目结构、配置文件、技术栈 | Implemented project analysis: auto-scans project structure, config files, tech stack
- 支持 27 种文档类型：README、LICENSE、.gitignore、CONTRIBUTING、CODE_OF_CONDUCT、CHANGELOG、SECURITY、SUPPORT、FUNDING.yml、GOVERNANCE、Issue 模板、PR 模板、.editorconfig、.gitattributes、CODEOWNERS、dependabot.yml、CITATION.cff、NOTICE、AUTHORS、MAINTAINERS、ARCHITECTURE、ROADMAP、FAQ、INSTALL、Dockerfile、docker-compose.yml、.env.example、Makefile | Supported 27 document types: README, LICENSE, .gitignore, CONTRIBUTING, CODE_OF_CONDUCT, CHANGELOG, SECURITY, SUPPORT, FUNDING.yml, GOVERNANCE, Issue templates, PR templates, .editorconfig, .gitattributes, CODEOWNERS, dependabot.yml, CITATION.cff, NOTICE, AUTHORS, MAINTAINERS, ARCHITECTURE, ROADMAP, FAQ, INSTALL, Dockerfile, docker-compose.yml, .env.example, Makefile
- 实现决策矩阵：根据项目特征智能选择所需文档 | Implemented decision matrix: intelligently selects required documents based on project characteristics
- 支持技术栈识别：Node.js、Python、Go、Rust、Java、C#/.NET、Godot、C/C++ | Supported tech stack identification: Node.js, Python, Go, Rust, Java, C#/.NET, Godot, C/C++
- 内置许可证选择指南：MIT、Apache-2.0、GPL-3.0、BSD-3-Clause、LGPL-3.0、AGPL-3.0、Unlicense | Built-in license selection guide: MIT, Apache-2.0, GPL-3.0, BSD-3-Clause, LGPL-3.0, AGPL-3.0, Unlicense
- 添加详细文件类型指南（references/file-types-guide.md），包含每种文件的完整内容结构和模板 | Added detailed file type guide (references/file-types-guide.md) with complete content structure and templates for each file type
- 添加质量检查清单 | Added quality checklist
