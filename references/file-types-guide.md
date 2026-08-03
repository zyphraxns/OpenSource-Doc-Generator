# 开源文档文件类型详细指南

本文件为 Skill 的参考资源，详细说明每种文档文件的内容结构、模板和最佳实践。Agent 在生成特定文件时，应阅读对应章节获取详细指导。

## 目录

- [1. README.md](#1-readmemd)
- [2. LICENSE](#2-license)
- [3. .gitignore](#3-gitignore)
- [4. CONTRIBUTING.md](#4-contributingmd)
- [5. CODE_OF_CONDUCT.md](#5-code_of_conductmd)
- [6. CHANGELOG.md](#6-changelogmd)
- [7. SECURITY.md](#7-securitymd)
- [8. SUPPORT.md](#8-supportmd)
- [9. FUNDING.yml](#9-fundingyml)
- [10. GOVERNANCE.md](#10-governancemd)
- [11. Issue 模板](#11-issue-模板)
- [12. PULL_REQUEST_TEMPLATE.md](#12-pull_request_templatemd)
- [13. .editorconfig](#13-editorconfig)
- [14. .gitattributes](#14-gitattributes)
- [15. CODEOWNERS](#15-codeowners)
- [16. dependabot.yml](#16-dependabotyml)
- [17. CITATION.cff](#17-citationcff)
- [18. NOTICE](#18-notice)
- [19. AUTHORS / MAINTAINERS.md](#19-authors--maintainersmd)
- [20. ARCHITECTURE.md](#20-architecturemd)
- [21. ROADMAP.md](#21-roadmapmd)
- [22. FAQ.md](#22-faqmd)
- [23. INSTALL.md](#23-installmd)
- [24. Dockerfile](#24-dockerfile)
- [25. docker-compose.yml](#25-docker-composeyml)
- [26. .env.example](#26-envexample)
- [27. Makefile](#27-makefile)

---

## 1. README.md

**路径**：仓库根目录
**重要性**：必需 — 项目最重要的文档，是用户的第一印象

### 内容结构

```markdown
# 项目名称

> 一句话描述项目做什么

[![CI Status](badge-url)](ci-url)
[![License: MIT](badge-url)](license-url)
[![Version](badge-url)](version-url)

## 简介

用 2-3 段话说明：
- 项目解决什么问题
- 为什么选择这个项目（核心价值/优势）
- 适用场景

## 功能特性

- 特性 1：简要说明
- 特性 2：简要说明
- 特性 3：简要说明

## 安装

### 前置要求

- Node.js >= 18 (或 Python >= 3.10 等具体版本)
- 其他系统依赖

### 安装步骤

\`\`\`bash
# 具体的安装命令
npm install project-name
# 或
pip install project-name
\`\`\`

## 快速开始

\`\`\`bash
# 最小可运行示例
\`\`\`

\`\`\`language
// 代码示例
\`\`\`

## 配置

说明配置文件、环境变量等（如有）：

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| PORT | number | 3000 | 服务端口 |
| DATABASE_URL | string | - | 数据库连接地址 |

## 文档

- [使用文档](docs/usage.md)
- [API 参考](docs/api.md)
- [常见问题](FAQ.md)

## 开发

请阅读 [CONTRIBUTING.md](CONTRIBUTING.md) 了解开发环境配置和贡献流程。

## 路线图

查看 [ROADMAP.md](ROADMAP.md) 了解项目未来计划。

## 贡献者

感谢所有为项目做出贡献的人（可使用 contrib.rocks 生成图片）。

## 许可证

本项目基于 [MIT](LICENSE) 许可证开源。
```

### 最佳实践

- 标题下方的一句话描述要精炼有力，直击痛点
- 安装命令要可以直接复制运行，包含所有前置步骤
- 快速开始示例要尽可能短，让用户 5 分钟内跑通
- 使用 Badge 增强视觉吸引力，但不要过多（3-5 个为宜）
- 如果项目有 UI，添加截图或 GIF 演示
- 保持 README 简洁，详细内容拆分到单独文档

---

## 2. LICENSE

**路径**：仓库根目录
**重要性**：必需 — 没有许可证的代码默认受著作权法保护，他人无权使用

### 内容

LICENSE 文件应包含完整的许可证文本，不是仅有许可证名称。常见许可证的全文可从以下来源获取：

- MIT: https://choosealicense.com/licenses/mit/
- Apache-2.0: https://choosealicense.com/licenses/apache-2.0/
- GPL-3.0: https://choosealicense.com/licenses/gpl-3.0/
- BSD-3-Clause: https://choosealicense.com/licenses/bsd-3-clause/
- LGPL-3.0: https://choosealicense.com/licenses/lgpl-3.0/
- AGPL-3.0: https://choosealicense.com/licenses/agpl-3.0/

### 生成要点

- MIT 和 BSD 许可证需要填入年份和版权持有者姓名
- Apache-2.0 许可证文本末尾需要附上 NOTICE 文件（如果项目使用了 Apache 代码）
- 许可证文本不要做任何修改，保持原文
- 如果项目使用双许可证，在 LICENSE 文件中说明，并在 README 中注明

### 示例（MIT）

```
MIT License

Copyright (c) [年份] [版权持有者姓名]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 3. .gitignore

**路径**：仓库根目录（可有多级）
**重要性**：必需

### 内容结构

根据项目技术栈，忽略以下类别的文件：

```gitignore
# 依赖目录
node_modules/
.venv/
vendor/

# 构建产物
dist/
build/
target/
*.class

# IDE 配置
.idea/
.vscode/
*.swp
*.swo
.DS_Store

# 环境变量和密钥
.env
.env.local
*.pem
*.key

# 日志
*.log
logs/

# 操作系统文件
Thumbs.db
.DS_Store

# 测试覆盖率
coverage/
.nyc_output/
.pytest_cache/

# 缓存
.cache/
__pycache__/
*.pyc
```

### 各技术栈补充

**Node.js**:
```gitignore
node_modules/
dist/
.env
npm-debug.log*
yarn-debug.log*
yarn-error.log*
.npm
.pnp.*
```

**Python**:
```gitignore
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
venv/
.venv/
*.egg-info/
dist/
build/
.pytest_cache/
.mypy_cache/
.tox/
.coverage
htmlcov/
```

**Go**:
```gitignore
*.exe
*.exe~
*.dll
*.so
*.dylib
*.test
*.out
vendor/
go.sum
```

**Rust**:
```gitignore
target/
*.pdb
```

**Java**:
```gitignore
target/
*.class
*.jar
*.war
*.ear
.gradle/
build/
!gradle-wrapper.jar
```

**C# / .NET**:
```gitignore
bin/
obj/
*.user
*.suo
.vs/
*.userprefs
*.cache
```

**Godot**:
```gitignore
.godot/
*.import
export_presets.cfg
.mono/
data_*/
```

---

## 4. CONTRIBUTING.md

**路径**：根目录（也可在 `.github/` 或 `docs/`）
**重要性**：强烈推荐 — GitHub 在创建 Issue/PR 时会自动链接此文件

### 内容结构

```markdown
# 贡献指南

感谢你对 [项目名称] 的关注！本文档将帮助你了解如何参与项目贡献。

## 行为准则

参与本项目即代表你同意遵守 [行为准则](CODE_OF_CONDUCT.md)。请在所有交流中保持尊重和友善。

## 如何贡献

### 报告 Bug

1. 先搜索现有 Issue，确认该 Bug 未被报告过
2. 使用 Bug 报告模板创建新 Issue
3. 提供以下信息：
   - 操作系统和版本
   - 项目版本
   - 复现步骤
   - 预期行为和实际行为
   - 错误日志/截图

### 提出功能建议

1. 先搜索现有 Issue，确认该建议未被提出过
2. 使用功能请求模板创建新 Issue
3. 说明：
   - 你想要的功能
   - 为什么需要这个功能（使用场景）
   - 你期望的实现方式

### 提交代码

#### 开发环境配置

\`\`\`bash
# 克隆仓库
git clone https://github.com/[org]/[repo].git
cd [repo]

# 安装依赖
npm install  # 或 pip install -e .[dev] 等

# 运行测试
npm test  # 或 pytest 等

# 启动开发服务器
npm run dev  # 或对应命令
\`\`\`

#### 开发流程

1. Fork 仓库并创建分支：
   \`\`\`bash
   git checkout -b feat/your-feature-name
   \`\`\`
2. 编写代码，确保：
   - 代码通过所有测试：`npm test`
   - 代码通过 lint 检查：`npm run lint`
   - 新功能有对应的测试用例
3. 提交代码，遵循 Conventional Commits 规范：
   \`\`\`
   feat: 添加用户登录功能
   fix: 修复登录页面样式错乱
   docs: 更新 README 安装说明
   refactor: 重构认证模块
   test: 增加登录功能的测试用例
   chore: 升级依赖版本
   \`\`\`
4. 推送并创建 Pull Request

#### 分支策略

- `main`：稳定发布分支
- `develop`：开发集成分支
- `feat/*`：新功能分支
- `fix/*`：Bug 修复分支
- `hotfix/*`：紧急修复分支

#### Pull Request 要求

- PR 标题遵循 Conventional Commits 规范
- 提供清晰的变更说明
- 关联相关 Issue（如 `Closes #123`）
- 确保 CI 检查通过
- 如果有 API 变更，更新对应文档

## 代码规范

- 使用 [ESLint/Prettier/Black/gofmt 等] 格式化代码
- 函数/类/变量命名要语义化
- 复杂逻辑需要添加注释
- 新增公开 API 需要添加 JSDoc/docstring

## 项目结构

\`\`\`
project/
├── src/          # 源代码
├── tests/        # 测试文件
├── docs/         # 文档
├── examples/     # 示例
└── scripts/      # 脚本
\`\`\`

## 联系方式

如有疑问，可以通过以下方式联系维护者：
- GitHub Issues
- 邮箱：[email]
- 社区频道：[Discord/Slack 链接]
```

---

## 5. CODE_OF_CONDUCT.md

**路径**：根目录
**重要性**：强烈推荐 — 社区健康的基础

### 内容结构

推荐使用 Contributor Covenant 模板（已被 Kubernetes、Rails、Swift 等数千个项目采用）：

```markdown
# 贡献者公约

## 我们的承诺

为了营造一个开放友好的环境，作为贡献者和维护者，我们承诺：参与我们项目的每个人
都不受骚扰和歧视，无论年龄、体型、残障状况、种族、性别特征、性别认同和表达、
经验水平、教育程度、社会经济地位、国籍、个人外貌、种族、种姓、肤色、宗教信仰、
性取向和性倾向。

我们承诺以促进开放、包容、多元化、健康社区的方式行事和互动。

## 我们的准则

营造正面环境的行为示例：

* 对他人展示同理心和善意
* 尊重不同意见、观点和经验
* 给予建设性反馈，也优雅地接受反馈
* 承担责任，向受我们错误影响的人道歉，并从中吸取经验
* 关注的不仅是个人，更是整个社区的福祉

不可接受的行为示例：

* 使用性化语言或意象，以及任何形式的性关注或骚扰
* 钓鱼、侮辱或贬损的评论，以及人身或政治攻击
* 公开或私下的骚扰
* 未经明确许可发布他人的私人信息
* 其他在专业环境中可以被合理认定为不当的行为

## 责任和权力

项目维护者有责任解释和落实本行为准则，并会对他们认为不当的威胁、冒犯
或有害的行为采取适当且公平的纠正措施。

## 适用范围

本行为准则适用于所有项目空间，当个人在公共空间中正式代表项目时，也代表项目
社区。

## 执行

辱骂、骚扰或其他不可接受的行为可通过 [联系方式] 向项目维护者报告。
所有投诉都将被及时、公正地审查和调查。

## 来源

本行为准则改编自 [Contributor Covenant][homepage] 2.1 版，
https://www.contributor-covenant.org/version/2/1/code_of_conduct.html

[homepage]: https://www.contributor-covenant.org
```

---

## 6. CHANGELOG.md

**路径**：根目录
**重要性**：强烈推荐 — 遵循 Keep a Changelog 规范

### 内容结构

```markdown
# 变更日志

本项目所有重要变更均会记录在此文件中。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，
版本管理遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

## [Unreleased]

### Added
- 待发布的新功能

## [1.0.0] - 2024-01-15

### Added
- 初始发布
- 支持 XXX 功能
- 添加 YYY 模块

### Changed
- 重构 ZZZ 模块，提升性能 30%

### Fixed
- 修复在 AAA 场景下的崩溃问题 (#123)

### Deprecated
- BBB 接口已废弃，将在 2.0.0 移除，请使用 CCC 替代

### Removed
- 移除了 DDD 功能（自 0.9.0 起已废弃）

### Security
- 修复 CVE-2024-XXXX 漏洞

## [0.9.0] - 2023-10-01

### Added
- 第一个 beta 版本
```

### 变更类别说明

| 类别 | 说明 |
|------|------|
| Added | 新增功能 |
| Changed | 对现有功能的变更 |
| Deprecated | 即将废弃的功能 |
| Removed | 已移除的功能（通常是之前 Deprecated 的） |
| Fixed | Bug 修复 |
| Security | 安全相关修复 |

---

## 7. SECURITY.md

**路径**：根目录（也可在 `.github/` 或 `docs/`）
**重要性**：推荐 — GitHub 会在 Security 标签页显示此文件

### 内容结构

```markdown
# 安全策略

## 报告安全漏洞

我们非常重视项目的安全问题。如果你发现安全漏洞，请按以下步骤报告：

### 不要公开

**请不要在 GitHub Issue 中公开报告安全漏洞。**

### 报告方式

1. 发送邮件至：[security@project.com]
2. 邮件主题请以 `[SECURITY]` 开头
3. 提供以下信息：
   - 漏洞描述
   - 复现步骤
   - 影响范围
   - 建议的修复方案（如有）

### 加密通信

如需加密通信，请使用以下 PGP 公钥：
\`\`\`
-----BEGIN PGP PUBLIC KEY BLOCK-----
[PGP 公钥内容]
-----END PGP PUBLIC KEY BLOCK-----
\`\`\`

## 响应时间

| 阶段 | 时间 |
|------|------|
| 确认收到报告 | 48 小时内 |
| 初步评估 | 7 天内 |
| 修复方案 | 30 天内（严重漏洞优先） |
| 补丁发布 | 修复完成后 7 天内 |

## 支持的版本

| 版本 | 支持状态 |
|------|----------|
| 1.x  | :white_check_mark: 安全更新 |
| 0.x  | :x: 不再支持 |

## 安全最佳实践

- 始终使用最新版本
- 不要在代码中硬编码密钥
- 使用环境变量管理敏感配置
- 定期更新依赖项
```

---

## 8. SUPPORT.md

**路径**：根目录（也可在 `.github/` 或 `docs/`）
**重要性**：推荐

### 内容结构

```markdown
# 获取帮助

在寻求帮助之前，请先查看以下资源：

## 文档

- [README](README.md) — 项目概述和快速开始
- [使用文档](docs/) — 详细使用说明
- [API 参考](docs/api.md) — API 文档
- [FAQ](FAQ.md) — 常见问题解答

## 提问

如果你遇到了问题：

1. **先搜索**：在 [GitHub Issues](issues-url) 中搜索是否有人已经遇到过相同问题
2. **提 Issue**：如果找不到解决方案，创建新 Issue
   - 使用 Issue 模板
   - 提供详细的问题描述、复现步骤和环境信息
3. **讨论区**：对于使用问题而非 Bug，请在 [GitHub Discussions](discussions-url) 中讨论

## 社区

- **Discord/Slack**：[加入链接]
- **Stack Overflow**：使用 `[project-name]` 标签提问

## 商业支持

如需商业支持，请联系：[email]

## 不要在这里报告的问题

以下情况请不要通过 Issue 报告：

- 安全漏洞 → 请阅读 [SECURITY.md](SECURITY.md)
- 功能建议 → 请使用功能请求模板
- 使用问题 → 请到 Discussions 讨论
```

---

## 9. FUNDING.yml

**路径**：`.github/FUNDING.yml`
**重要性**：可选 — 在仓库显示 Sponsor 按钮

### 内容结构

```yaml
# GitHub Sponsors
github: [username]

# Patreon
patreon: [username]

# Open Collective
open_collective: [project-name]

# Ko-fi
ko_fi: [username]

# Tidelift
tidelift: [npm/project-name]

# Community Bridge
community_bridge: [project-name]

# Liberapay
liberapay: [username]

# IssueHunt
issuehunt: [username]

# Otechie
otechie: [username]

# 自定义链接（最多 4 个）
custom: ["https://example.com/donate", "https://example.com/wishlist"]
```

### 说明

只需填写你实际使用的赞助平台，不需要全部填满。

---

## 10. GOVERNANCE.md

**路径**：根目录
**重要性**：推荐 — 适用于多人维护的中大型项目

### 内容结构

```markdown
# 项目治理

## 角色

### 贡献者 (Contributor)

任何提交并合并了 PR 的人都是贡献者。贡献者权利：
- 提交 Issue 和 PR
- 参与设计讨论
- 评审他人的 PR

### 提交者 (Committer)

有仓库写权限的成员。获得条件：
- 持续贡献高质量代码 3 个月以上
- 获得 2 名以上维护者推荐
- 熟悉项目代码规范和架构

提交者权利：
- 贡献者的所有权利
- 合并 PR
- 创建分支和标签

### 维护者 (Maintainer)

有仓库管理权限的成员。获得条件：
- 担任提交者 6 个月以上
- 获得 2 名以上维护者推荐
- 展现出对项目方向的理解和判断力

维护者权利：
- 提交者的所有权利
- 发布版本
- 管理 Issue 和 PR 标签
- 参与项目路线图决策

## 决策流程

### 小范围决策

由相关模块的提交者/维护者讨论决定。

### 大范围决策

影响项目方向的重大决策（如架构调整、许可证变更等）：
1. 提出 RFC (Request for Comments)
2. 社区讨论（至少 2 周）
3. 维护者投票（简单多数通过）
4. 公布决策结果

### 投票机制

- +1：赞成
- 0：中立
- -1：反对（需说明理由）
- 决策需获得简单多数（>50%）赞成票

## 升级和降级

- 升级：满足条件后由现有维护者提名和投票
- 降级：长期不活跃（6 个月以上）的提交者/维护者将转为荣誉成员
```

---

## 11. Issue 模板

**路径**：`.github/ISSUE_TEMPLATE/`
**重要性**：推荐

### Bug 报告模板 (`.github/ISSUE_TEMPLATE/bug_report.md`)

```markdown
---
name: Bug 报告
about: 报告一个 Bug 帮助我们改进
title: '[BUG] '
labels: bug
assignees: ''
---

## Bug 描述

简要描述遇到了什么问题。

## 复现步骤

1. 进入 '...'
2. 点击 '...'
3. 滚动到 '...'
4. 看到错误

## 预期行为

描述你期望发生什么。

## 实际行为

描述实际发生了什么。

## 环境

- 操作系统：[例如 macOS 14.0, Ubuntu 22.04]
- 项目版本：[例如 1.2.3]
- 运行时版本：[例如 Node.js 18.17.0, Python 3.11.4]
- 浏览器（如适用）：[例如 Chrome 120]

## 截图/日志

如果有截图或错误日志，请附上。

## 附加信息

其他可能有助于诊断问题的信息。
```

### 功能请求模板 (`.github/ISSUE_TEMPLATE/feature_request.md`)

```markdown
---
name: 功能请求
about: 建议一个新功能或改进
title: '[FEATURE] '
labels: enhancement
assignees: ''
---

## 功能描述

简要描述你希望添加的功能。

## 解决的问题

这个功能要解决什么问题？（例如："每次我需要做 X 时都很不方便，因为..."）

## 建议的方案

描述你期望的解决方案。

## 替代方案

你考虑过的其他方案。

## 附加信息

其他相关截图、链接或信息。
```

### Issue 模板配置 (`.github/ISSUE_TEMPLATE/config.yml`)

```yaml
blank_issues_enabled: false
contact_links:
  - name: 使用问题
    url: https://github.com/org/repo/discussions
    about: 使用问题请在 Discussions 中讨论
  - name: 安全漏洞
    url: https://github.com/org/repo/security/policy
    about: 安全漏洞请查看安全策略
```

---

## 12. PULL_REQUEST_TEMPLATE.md

**路径**：`.github/PULL_REQUEST_TEMPLATE.md`
**重要性**：推荐

### 内容结构

```markdown
## 变更说明

简要描述本 PR 做了什么改动。

## 变更类型

- [ ] Bug 修复 (fix)
- [ ] 新功能 (feat)
- [ ] 破坏性变更 (BREAKING CHANGE)
- [ ] 文档更新 (docs)
- [ ] 重构 (refactor)
- [ ] 性能优化 (perf)
- [ ] 测试 (test)
- [ ] 构建/CI (chore)

## 关联 Issue

Closes #（issue 编号）

## 检查清单

- [ ] 代码通过 lint 检查
- [ ] 代码通过所有测试
- [ ] 新功能有对应的测试用例
- [ ] 文档已更新（如需要）
- [ ] 提交信息遵循 Conventional Commits 规范
- [ ] 没有引入新的警告

## 截图/演示

如有 UI 变更，请附上截图或录屏。

## 破坏性变更

如果本 PR 包含破坏性变更，请说明：
- 变更内容
- 迁移指南
- 影响范围
```

---

## 13. .editorconfig

**路径**：根目录
**重要性**：推荐 — 多人协作时统一代码风格

### 内容结构

```ini
# EditorConfig: https://editorconfig.org
# 帮助不同编辑器/IDE 维护一致的编码风格

root = true

# 所有文件
[*]
charset = utf-8
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true
indent_style = space
indent_size = 2

# Python 文件
[*.py]
indent_size = 4

# Go 文件
[*.go]
indent_style = tab

# Markdown 文件（保留尾部空格）
[*.md]
trim_trailing_whitespace = false

# Makefile（必须用 tab）
[Makefile]
indent_style = tab

# YAML 文件
[*.{yml,yaml}]
indent_size = 2

# JSON 文件
[*.json]
indent_size = 2
```

---

## 14. .gitattributes

**路径**：根目录
**重要性**：推荐 — 跨平台协作和语言统计修正

### 内容结构

```gitattributes
# 统一换行符
* text=auto eol=lf

# 特定文件类型
*.bat text eol=crlf
*.sh text eol=lf
*.ps1 text eol=crlf

# 二进制文件
*.png binary
*.jpg binary
*.gif binary
*.ico binary
*.pdf binary
*.zip binary

# 语言统计修正（避免将某些文件计入语言统计）
docs/* linguist-documentation
*.min.js linguist-generated
*.lock linguist-generated

# 导出忽略（git archive 时不包含）
.gitattributes export-ignore
.gitignore export-ignore
.github export-ignore
tests export-ignore
```

---

## 15. CODEOWNERS

**路径**：`.github/CODEOWNERS`（也可在根目录）
**重要性**：推荐 — GitHub 自动请求代码所有者评审

### 内容结构

```gitowners
# 每行格式：文件路径模式 @用户名 @团队名

# 默认所有者
* @maintainer1 @maintainer2

# 前端代码
/src/frontend/ @frontend-team @maintainer1

# 后端代码
/src/backend/ @backend-team @maintainer2

# 基础设施
/.github/ @devops-team
/Dockerfile @devops-team
/docker-compose.yml @devops-team

# 文档
/docs/ @docs-team @maintainer1
*.md @docs-team

# 测试
/tests/ @qa-team
```

---

## 16. dependabot.yml

**路径**：`.github/dependabot.yml`
**重要性**：可选 — 自动依赖更新

### 内容结构

```yaml
version: 2
updates:
  # npm 依赖
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
      day: "monday"
    open-pull-requests-limit: 10
    reviewers:
      - "maintainer-name"
    labels:
      - "dependencies"
      - "npm"
    commit-message:
      prefix: "chore(deps)"

  # pip 依赖
  - package-ecosystem: "pip"
    directory: "/"
    schedule:
      interval: "weekly"
    labels:
      - "dependencies"
      - "pip"

  # GitHub Actions
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "monthly"
    labels:
      - "dependencies"
      - "github-actions"

  # Docker 基础镜像
  - package-ecosystem: "docker"
    directory: "/"
    schedule:
      interval: "monthly"
    labels:
      - "dependencies"
      - "docker"
```

---

## 17. CITATION.cff

**路径**：根目录
**重要性**：特定场景 — 学术/科研项目

### 内容结构

```yaml
cff-version: 1.2.0
message: "如果您使用了本项目，请按以下方式引用。"
title: "项目名称"
authors:
  - given-names: "名"
    family-names: "姓"
    orcid: "https://orcid.org/0000-0000-0000-0000"
    affiliation: "所属机构"
version: "1.0.0"
date-released: "2024-01-15"
doi: "10.5281/zenodo.xxxxxxx"
license: "MIT"
repository-code: "https://github.com/org/repo"
url: "https://project-website.com"
keywords:
  - "关键词1"
  - "关键词2"
preferred-citation:
  type: "software"
  authors:
    - given-names: "名"
      family-names: "姓"
  title: "项目名称"
  year: 2024
```

---

## 18. NOTICE

**路径**：根目录
**重要性**：特定场景 — Apache-2.0 许可证或包含第三方代码

### 内容结构

```
项目名称
Copyright 2024 [版权持有者]

该产品包含由 Apache Software Foundation 开发的软件
(https://www.apache.org/).

该产品包含以下第三方组件：

1. Component Name
   Copyright [年份] [作者]
   License: [许可证名称]
   URL: [项目地址]

2. Another Component
   Copyright [年份] [作者]
   License: [许可证名称]
```

---

## 19. AUTHORS / MAINTAINERS.md

**路径**：根目录
**重要性**：可选

### AUTHORS

```
# 按字母顺序排列

John Doe <john@example.com>
Jane Smith <jane@example.com>
张三 <zhangsan@example.com>
```

### MAINTAINERS.md

```markdown
# 维护者

## 当前维护者

| 姓名 | 角色 | GitHub |
|------|------|--------|
| 张三 | 项目负责人 | @zhangsan |
| 李四 | 核心维护者 | @lisi |
| 王五 | 维护者 | @wangwu |

## 荣誉维护者

| 姓名 | 贡献 | GitHub |
|------|------|--------|
| 赵六 | 前核心维护者 | @zhaoliu |

## 联系方式

- 安全问题：security@project.com
- 一般问题：通过 GitHub Issues
```

---

## 20. ARCHITECTURE.md

**路径**：根目录
**重要性**：特定场景 — 中大型项目

### 内容结构

```markdown
# 架构设计

## 概述

[项目名称] 采用 [架构风格] 架构，主要分为以下模块：

## 系统架构图

\`\`\`
┌──────────┐    ┌──────────┐    ┌──────────┐
│  前端 UI  │───→│  API 层   │───→│ 数据存储  │
└──────────┘    └──────────┘    └──────────┘
                      │
                      ↓
                ┌──────────┐
                │ 任务队列  │
                └──────────┘
\`\`\`

## 模块说明

### 前端 (frontend/)
- 技术栈：[框架]
- 职责：用户界面渲染、交互处理

### API 层 (api/)
- 技术栈：[框架]
- 职责：请求路由、业务逻辑、数据校验

### 数据层 (data/)
- 技术栈：[数据库]
- 职责：数据持久化、缓存

## 数据流

1. 用户通过前端发起请求
2. API 层接收请求，进行认证和参数校验
3. 业务逻辑处理后，读写数据层
4. 异步任务进入任务队列
5. 返回响应给前端

## 设计决策

### 为什么选择 [技术] 而不是 [替代方案]？

[决策原因和权衡]

### 为什么使用 [架构模式]？

[决策原因和权衡]

## 扩展性考虑

- [如何水平扩展]
- [如何添加新模块]
- [数据分片策略]
```

---

## 21. ROADMAP.md

**路径**：根目录
**重要性**：可选

### 内容结构

```markdown
# 项目路线图

## 当前版本：v1.0.0 (2024 Q1)

- [x] 核心功能 A
- [x] 核心功能 B
- [x] 基础文档和测试

## 下一版本：v1.1.0 (2024 Q2)

- [ ] 性能优化
- [ ] 功能 C
- [ ] 插件系统

## 未来计划

### v2.0.0 (2024 Q4)
- [ ] 架构重构
- [ ] 功能 D
- [ ] 多语言支持

### 探索中
- [ ] 功能 E
- [ ] F 集成

## 版本规划原则

- 遵循语义化版本 (SemVer)
- 小版本每 [周期] 发布一次
- 大版本视项目进展决定
- 路线图会根据社区反馈调整
```

---

## 22. FAQ.md

**路径**：根目录
**重要性**：可选

### 内容结构

```markdown
# 常见问题

## 安装相关

### Q: 安装时报 `error: XXX` 怎么办？

A: 这通常是因为 [原因]。请尝试：
1. 检查 Node.js 版本是否 >= 18
2. 清除缓存：`npm cache clean --force`
3. 重新安装：`rm -rf node_modules && npm install`

### Q: 支持 Windows 吗？

A: 支持。但建议使用 WSL2 以获得最佳体验。

## 使用相关

### Q: 如何自定义 XXX 配置？

A: 在配置文件中设置 `xxx` 选项：
\`\`\`yaml
xxx:
  enabled: true
  value: "custom"
\`\`\`

### Q: 数据存在哪里？

A: 默认存储在 `~/.project/data/` 目录，可通过环境变量 `DATA_DIR` 修改。

## 开发相关

### Q: 如何运行测试？

A: \`\`\`bash
npm test          # 运行所有测试
npm run test:unit # 单元测试
npm run test:e2e  # 端到端测试
\`\`\`

### Q: 如何添加新功能？

A: 请阅读 [CONTRIBUTING.md](CONTRIBUTING.md) 了解开发流程。

## 其他

### Q: 项目和其他类似项目有什么区别？

A: [简要说明差异化优势]

### Q: 有商业版吗？

A: [说明商业模式或声明无商业版]
```

---

## 23. INSTALL.md

**路径**：根目录
**重要性**：特定场景 — 当 README 中的安装部分过长时拆分

### 内容结构

```markdown
# 安装指南

## 系统要求

| 要求 | 最低版本 | 推荐版本 |
|------|----------|----------|
| OS | macOS 12 / Ubuntu 20.04 / Windows 10 | 最新版本 |
| 运行时 | Node.js 18 | Node.js 20 LTS |
| 内存 | 512MB | 2GB+ |
| 磁盘 | 100MB | 1GB+ |

## 安装方式

### 方式一：包管理器安装（推荐）

\`\`\`bash
# npm
npm install -g project-name

# yarn
yarn global add project-name

# pnpm
pnpm add -g project-name
\`\`\`

### 方式二：源码编译

\`\`\`bash
# 克隆仓库
git clone https://github.com/org/repo.git
cd repo

# 安装依赖
npm install

# 编译
npm run build

# 全局链接
npm link
\`\`\`

### 方式三：Docker

\`\`\`bash
docker pull org/project-name:latest
docker run -d -p 3000:3000 org/project-name
\`\`\`

## 验证安装

\`\`\`bash
project-name --version
\`\`\`

如果输出版本号，说明安装成功。

## 平台特定说明

### macOS

使用 Homebrew 安装：
\`\`\`bash
brew install project-name
\`\`\`

### Linux

\`\`\`bash
# 下载二进制文件
curl -L https://github.com/org/repo/releases/latest/download/project-linux-amd64 -o /usr/local/bin/project-name
chmod +x /usr/local/bin/project-name
\`\`\`

### Windows

从 [Releases](releases-url) 下载 `.exe` 安装包。

## 卸载

\`\`\`bash
npm uninstall -g project-name
\`\`\`

## 故障排除

### 权限错误 (EACCES)

\`\`\`bash
# 方案一：使用 nvm 管理 Node.js
# 方案二：修改 npm 全局安装目录
npm config set prefix ~/.npm-global
export PATH=~/.npm-global/bin:$PATH
\`\`\`

### 网络超时

\`\`\`bash
# 使用镜像源
npm install -g project-name --registry=https://registry.npmmirror.com
\`\`\`
```

---

## 24. Dockerfile

**路径**：根目录
**重要性**：特定场景

### 内容结构（多阶段构建示例）

```dockerfile
# 构建阶段
FROM node:20-alpine AS builder

WORKDIR /app

# 安装依赖
COPY package*.json ./
RUN npm ci

# 复制源码并构建
COPY . .
RUN npm run build

# 运行阶段
FROM node:20-alpine AS runner

WORKDIR /app

ENV NODE_ENV=production

# 只复制必要文件
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package.json ./

# 暴露端口
EXPOSE 3000

# 健康检查
HEALTHCHECK --interval=30s --timeout=3s --retries=3 \
  CMD wget --no-verbose --tries=1 --spider http://localhost:3000/health || exit 1

# 非 root 用户运行
USER node

CMD ["node", "dist/index.js"]
```

### 生成要点

- 使用多阶段构建减小镜像体积
- 使用 Alpine 基础镜像
- 以非 root 用户运行
- 添加 HEALTHCHECK
- 合理利用 Docker 层缓存（先 COPY 依赖文件，再 COPY 源码）
- 根据项目实际技术栈调整

---

## 25. docker-compose.yml

**路径**：根目录
**重要性**：特定场景

### 内容结构

```yaml
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - DATABASE_URL=postgresql://user:pass@db:5432/dbname
      - REDIS_URL=redis://redis:6379
    depends_on:
      db:
        condition: service_healthy
      redis:
        condition: service_started
    restart: unless-stopped

  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: pass
      POSTGRES_DB: dbname
    volumes:
      - db_data:/var/lib/postgresql/data
    ports:
      - "5432:5432"
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U user -d dbname"]
      interval: 10s
      timeout: 5s
      retries: 5

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data

volumes:
  db_data:
  redis_data:
```

---

## 26. .env.example

**路径**：根目录
**重要性**：特定场景 — 项目使用环境变量时

### 内容结构

```bash
# 服务配置
PORT=3000
HOST=0.0.0.0
NODE_ENV=development

# 数据库
DATABASE_URL=postgresql://user:password@localhost:5432/dbname

# Redis
REDIS_URL=redis://localhost:6379

# 认证
JWT_SECRET=your-jwt-secret-here
JWT_EXPIRES_IN=7d

# 第三方服务
SMTP_HOST=smtp.example.com
SMTP_PORT=587
SMTP_USER=your-email@example.com
SMTP_PASS=your-email-password

# API 密钥（仅示例，不要使用真实密钥）
API_KEY=your-api-key-here

# 日志
LOG_LEVEL=debug
```

### 生成要点

- 包含所有项目需要的环境变量
- 使用示例值，不要使用真实密钥
- 按功能分组并添加注释
- 在 .gitignore 中确保 .env 被忽略

---

## 27. Makefile

**路径**：根目录
**重要性**：特定场景 — 有构建/测试流程的项目

### 内容结构

```makefile
.PHONY: install dev build test lint clean docker-build docker-up docker-down help

# 默认目标
.DEFAULT_GOAL := help

# 变量
VERSION := $(shell git describe --tags --always --dirty 2>/dev/null || echo "dev")
DOCKER_IMAGE := project-name

help: ## 显示帮助信息
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | \
		awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-20s\033[0m %s\n", $$1, $$2}'

install: ## 安装依赖
	npm install

dev: ## 启动开发服务器
	npm run dev

build: ## 构建项目
	npm run build

test: ## 运行测试
	npm test

test-coverage: ## 运行测试并生成覆盖率报告
	npm run test:coverage

lint: ## 代码检查
	npm run lint

lint-fix: ## 自动修复代码风格
	npm run lint:fix

clean: ## 清理构建产物
	rm -rf dist node_modules/.cache

docker-build: ## 构建 Docker 镜像
	docker build -t $(DOCKER_IMAGE):$(VERSION) .

docker-up: ## 启动 Docker 容器
	docker compose up -d

docker-down: ## 停止 Docker 容器
	docker compose down

release: ## 发布新版本
	@echo "当前版本: $(VERSION)"
	@read -p "输入新版本号: " new_version; \
	git tag -a v$$new_version -m "Release v$$new_version"; \
	git push origin v$$new_version
```

### 生成要点

- 始终包含 `help` 目标
- 使用 `.PHONY` 声明非文件目标
- 命令要和项目实际的构建/测试命令一致
- 目标名称要语义化
```
