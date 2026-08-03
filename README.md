# opensource-doc-generator

> 一个 TRAE Work Skill，根据项目文件自动生成开源平台（GitHub / GitLab / Gitee）所需的各种说明文档。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![TRAE Work Skill](https://img.shields.io/badge/TRAE%20Work-Skill-blue.svg)](https://www.trae.cn/)

## 简介

`opensource-doc-generator` 是一个 [TRAE Work](https://www.trae.cn/) Skill，帮助 Agent 根据项目的实际文件和结构，为开源平台生成全套规范的说明文档。

核心思路：**先分析项目，再智能选择所需文档类型，最后逐一生成**。

开源项目的文档质量直接影响项目的采纳率、贡献者增长和社区健康度。一份好的 README 可以让用户在 30 秒内理解项目价值；一份清晰的 CONTRIBUTING 可以降低 50% 的贡献者入门成本；而缺少 LICENSE 的项目在法律意义上根本不算开源。

## 功能特性

- **智能项目分析** — 自动扫描项目结构、配置文件、技术栈，提取项目名称、版本、依赖等关键信息
- **20+ 种文档类型** — 覆盖 README、LICENSE、CONTRIBUTING、CHANGELOG、CODE_OF_CONDUCT、SECURITY、Issue 模板、PR 模板等全部常见开源文档
- **决策矩阵驱动** — 根据项目特征（是否接受贡献、是否有版本发布、是否处理敏感数据等）智能选择需要的文档，不会一刀切
- **技术栈感知** — 自动识别 Node.js / Python / Go / Rust / Java / C# / Godot 等技术栈，生成对应的 .gitignore 规则
- **许可证选择指南** — 内置 MIT / Apache-2.0 / GPL-3.0 / BSD / LGPL / AGPL 等许可证的适用场景说明
- **详细内容指南** — 每种文档类型都有完整的内容结构模板和最佳实践建议（见 `references/file-types-guide.md`）
- **质量检查清单** — 生成后自动检查文档完整性、交叉引用一致性、占位符残留等

## 安装

### 方式一：手动安装

将本仓库克隆到本地，然后把 `opensource-doc-generator` 文件夹复制到 TRAE Work 的 Skills 目录：

```bash
git clone https://github.com/zyphraxns/opensource-doc-generator.git
cp -r opensource-doc-generator ~/.trae-cn/skills/
```

### 方式二：直接下载

1. 下载本仓库的 ZIP 包
2. 解压后将 `opensource-doc-generator` 文件夹放入 `~/.trae-cn/skills/` 目录

安装完成后，Skill 会在下次 TRAE Work 会话中自动加载。

## 快速开始

安装 Skill 后，在 TRAE Work 中直接用自然语言触发即可：

```
帮我的项目生成开源文档
```

或者更具体地：

```
我要把项目上传到 GitHub，帮我生成 README 和其他需要的文档
```

Skill 会自动分析你的项目并生成所需的文档文件。

## 目录结构

```
opensource-doc-generator/
├── SKILL.md                         # Skill 主文件（工作流、文档目录、决策矩阵）
├── references/
│   └── file-types-guide.md          # 27 种文档类型的详细内容指南和模板
├── README.md                        # 你正在看的这个文件
├── LICENSE                          # MIT 许可证
├── CONTRIBUTING.md                  # 贡献指南
├── CODE_OF_CONDUCT.md               # 行为准则
├── CHANGELOG.md                     # 变更日志
├── .gitignore                       # Git 忽略规则
├── .editorconfig                    # 编辑器配置
├── .gitattributes                   # Git 属性配置
└── .github/
    ├── PULL_REQUEST_TEMPLATE.md     # PR 模板
    └── ISSUE_TEMPLATE/
        ├── bug_report.md            # Bug 报告模板
        ├── feature_request.md       # 功能请求模板
        └── config.yml               # Issue 模板配置
```

## 支持的文档类型

| 类别 | 文件 | 说明 |
|------|------|------|
| **必需** | `README.md` | 项目门面，第一入口 |
| **必需** | `LICENSE` | 开源许可证 |
| **必需** | `.gitignore` | Git 忽略规则 |
| **强烈推荐** | `CONTRIBUTING.md` | 贡献指南 |
| **强烈推荐** | `CODE_OF_CONDUCT.md` | 行为准则 |
| **强烈推荐** | `CHANGELOG.md` | 变更日志 |
| **社区健康** | `SECURITY.md` | 安全策略 |
| **社区健康** | `SUPPORT.md` | 支持资源 |
| **社区健康** | `FUNDING.yml` | 赞助配置 |
| **社区健康** | `GOVERNANCE.md` | 项目治理 |
| **社区健康** | `ISSUE_TEMPLATE/` | Issue 模板 |
| **社区健康** | `PULL_REQUEST_TEMPLATE.md` | PR 模板 |
| **配置** | `.editorconfig` | 编辑器风格统一 |
| **配置** | `.gitattributes` | Git 文件属性 |
| **配置** | `CODEOWNERS` | 代码所有者 |
| **配置** | `dependabot.yml` | 依赖自动更新 |
| **场景** | `CITATION.cff` | 学术引用 |
| **场景** | `NOTICE` | 归属声明 |
| **场景** | `ARCHITECTURE.md` | 架构文档 |
| **场景** | `ROADMAP.md` | 路线图 |
| **场景** | `FAQ.md` | 常见问题 |
| **场景** | `INSTALL.md` | 安装指南 |
| **场景** | `Dockerfile` | Docker 部署 |
| **场景** | `docker-compose.yml` | Docker 编排 |
| **场景** | `.env.example` | 环境变量示例 |
| **场景** | `Makefile` | 构建自动化 |

## 工作流程

Skill 触发后会执行四个步骤：

1. **项目分析** — 扫描配置文件、技术栈、目录结构、现有文档，判断项目类型和特征
2. **文档选择** — 基于决策矩阵，根据项目特征智能选择所需文档（不会一刀切创建所有文件）
3. **文档生成** — 读取参考指南，结合项目实际信息逐一生成，内容具体准确
4. **总结报告** — 列出已创建文件、建议补充内容、未创建文件及原因

## 许可证

本项目基于 [MIT License](LICENSE) 开源。
