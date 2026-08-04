# 变更日志

本项目所有重要变更均会记录在此文件中。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，
版本管理遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

## [Unreleased]

## [1.1.0] - 2026-08-04

### Added
- 新增第三步「用户确认与选择」交互步骤，在生成文件前向用户展示：
  - 项目分析摘要（让用户确认 AI 理解是否正确）
  - 3-4 个分级推荐方案（全套/标准/基础/最小），每个方案包含文件清单和说明
  - 需要用户确认的问题（许可证类型、文档语言、作者信息等）
- 新增「分级推荐方案设计指南」，明确各方案应包含的文件范围
- 决策矩阵新增「项目特征 → 方案一/方案二额外包含」对照表
- 质量检查清单新增三项检查（许可证类型一致性、文档语言一致性、已有文件不被覆盖）

### Changed
- 工作流程从 4 步扩展为 5 步：项目分析 → 智能推荐分级 → 用户确认与选择 → 文档生成 → 总结报告
- 核心思路更新为"先分析项目，再智能推荐分级方案，经用户确认后逐一生成"
- 决策矩阵说明更新为"内部参考，最终创建哪些文件由用户决定"
- 输出格式从 3 项扩展为 5 项

### Reorganized
- 将 V1 版本文件移入 `V1/` 目录
- V2 版本文件放入 `V2/` 目录
- 根目录保留项目级文档（README、LICENSE、CONTRIBUTING 等）

## [1.0.0] - 2026-08-03

### Added
- 初始发布
- 实现项目分析功能：自动扫描项目结构、配置文件、技术栈
- 支持 27 种文档类型：README、LICENSE、.gitignore、CONTRIBUTING、CODE_OF_CONDUCT、CHANGELOG、SECURITY、SUPPORT、FUNDING.yml、GOVERNANCE、Issue 模板、PR 模板、.editorconfig、.gitattributes、CODEOWNERS、dependabot.yml、CITATION.cff、NOTICE、AUTHORS、MAINTAINERS、ARCHITECTURE、ROADMAP、FAQ、INSTALL、Dockerfile、docker-compose.yml、.env.example、Makefile
- 实现决策矩阵：根据项目特征智能选择所需文档
- 支持技术栈识别：Node.js、Python、Go、Rust、Java、C#/.NET、Godot、C/C++
- 内置许可证选择指南：MIT、Apache-2.0、GPL-3.0、BSD-3-Clause、LGPL-3.0、AGPL-3.0、Unlicense
- 添加详细文件类型指南（references/file-types-guide.md），包含每种文件的完整内容结构和模板
- 添加质量检查清单
