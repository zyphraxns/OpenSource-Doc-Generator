---
name: opensource-doc-generator
description: |
  根据项目文件自动生成开源平台（如 GitHub）所需的各种说明文档。扫描项目结构、代码和技术栈，智能判断需要创建哪些文档文件（README、LICENSE、CONTRIBUTING、CHANGELOG、CODE_OF_CONDUCT、SECURITY 等 20+ 种），并为每种文件生成符合规范的内容。
  当用户提到"开源文档"、"README"、"上传到 GitHub"、"准备开源"、"项目说明文件"、"文档生成"、"开源准备"、"CONTRIBUTING"、"LICENSE 文件"、"CHANGELOG"等意图时，务必使用此 Skill。即使用户只是说"帮我的项目写个说明"或"我想把项目开源"，也应触发此 Skill。
---

# 开源文档生成器 (Open Source Documentation Generator)

## 概述

本 Skill 帮助 Agent 根据项目的实际文件和结构，为开源平台（如 GitHub、GitLab、Gitee 等）生成全套规范的说明文档。核心思路是：**先分析项目，再智能选择所需文档类型，最后逐一生成**。

开源项目的文档质量直接影响项目的采纳率、贡献者增长和社区健康度。一份好的 README 可以让用户在 30 秒内理解项目价值；一份清晰的 CONTRIBUTING 可以降低 50% 的贡献者入门成本；而缺少 LICENSE 的项目在法律意义上根本不算开源。

## 工作流程

### 第一步：项目分析

深入扫描项目，收集以下信息：

1. **项目基本信息**
   - 项目名称（从 `package.json`、`pyproject.toml`、`Cargo.toml`、`go.mod`、`pom.xml`、`*.csproj` 等配置文件中提取）
   - 项目描述和用途
   - 版本号
   - 作者/维护者信息

2. **技术栈识别**
   - 编程语言（通过文件扩展名和配置文件判断）
   - 框架和库（从依赖文件中提取：`package.json`、`requirements.txt`、`Pipfile`、`go.sum`、`Cargo.lock` 等）
   - 构建工具（Webpack、Vite、CMake、Makefile、Gradle 等）
   - 测试框架（Jest、Pytest、Go test 等）
   - CI/CD 配置（是否已有 `.github/workflows/`、`.gitlab-ci.yml` 等）

3. **项目结构分析**
   - 目录结构（源码、文档、测试、配置等目录的分布）
   - 入口文件（`main.py`、`index.js`、`src/main.rs`、`cmd/main.go` 等）
   - 文档目录（`docs/`、`wiki/` 等）
   - 示例代码（`examples/`、`demo/` 等）

4. **现有文档检查**
   - 检查项目根目录和 `.github/` 目录下已存在哪些文档文件
   - 检查 `.gitignore`、`.editorconfig` 等配置文件是否已存在
   - 检查是否已有 LICENSE 文件

5. **项目特征判断**
   - 是否是库/框架（供其他项目依赖）
   - 是否是独立应用/工具
   - 是否是学术/科研项目
   - 是否有 Docker 支持
   - 是否有多语言支持
   - 项目规模（小型/中型/大型）

### 第二步：文档类型选择

根据项目分析结果，参照下文的**文档类型目录**和**决策矩阵**，确定需要创建的文档文件。

选择原则：
- **必需文件**：无论什么项目都应创建（README、LICENSE、.gitignore）
- **推荐文件**：根据项目特征判断是否需要（CONTRIBUTING、CHANGELOG、CODE_OF_CONDUCT 等）
- **场景文件**：仅在特定场景下创建（CITATION.cff、NOTICE、GOVERNANCE.md 等）

如果用户已有部分文件，**不要覆盖**，而是在分析报告中指出可以改进的地方。

### 第三步：文档生成

对每个选定的文档类型：

1. 阅读 `references/file-types-guide.md` 中对应章节，了解该文件的详细内容要求和模板
2. 结合第一步收集的项目信息，填充具体内容
3. 生成文件到正确路径（根目录或 `.github/` 目录）
4. 对生成的内容进行质量检查

生成原则：
- 内容要**具体且准确**，基于项目的实际代码和配置，不要使用空洞的模板化语言
- 使用项目实际的命令、路径、依赖名称
- 保持文档语言与项目代码注释/现有文档的语言一致（如果项目是中文注释，文档也用中文；英文注释则用英文）
- 文件之间的交叉引用要保持一致（如 README 中引用 LICENSE、CONTRIBUTING 等）

### 第四步：生成总结报告

生成所有文件后，向用户输出一份总结报告，包括：
- 创建了哪些文件及其路径
- 每个文件的简要说明
- 建议后续手动补充的内容（如需要用户提供的特定信息）
- 未创建但可能需要的文件及原因

---

## 文档类型目录

以下按优先级分类列出所有可能需要的文档文件。详细的内容指南请阅读 `references/file-types-guide.md`。

### 第一类：必需文件 (Required)

| 文件 | 路径 | 说明 |
|------|------|------|
| `README.md` | 根目录 | 项目门面，第一入口。包含项目简介、功能特性、安装方法、使用示例、配置说明等 |
| `LICENSE` | 根目录 | 开源许可证。没有许可证的代码默认受著作权法保护，他人无权使用 |
| `.gitignore` | 根目录 | Git 忽略规则，排除构建产物、依赖、密钥等不应提交的文件 |

### 第二类：强烈推荐 (Strongly Recommended)

| 文件 | 路径 | 说明 |
|------|------|------|
| `CONTRIBUTING.md` | 根目录 | 贡献指南，说明如何提交 Issue、PR、开发环境配置、代码规范等 |
| `CODE_OF_CONDUCT.md` | 根目录 | 行为准则，定义社区参与标准，营造友好的协作环境 |
| `CHANGELOG.md` | 根目录 | 变更日志，按版本记录新增、修改、修复、移除等变更 |

### 第三类：GitHub 社区健康文件 (Recommended)

| 文件 | 路径 | 说明 |
|------|------|------|
| `SECURITY.md` | 根目录 | 安全策略，说明如何报告安全漏洞 |
| `SUPPORT.md` | 根目录 | 支持资源，告知用户获取帮助的途径 |
| `FUNDING.yml` | `.github/` | 赞助配置，在仓库显示 Sponsor 按钮 |
| `GOVERNANCE.md` | 根目录 | 项目治理，说明角色定义和决策流程 |
| `ISSUE_TEMPLATE/` | `.github/` | Issue 模板（Bug 报告、功能请求等） |
| `PULL_REQUEST_TEMPLATE.md` | `.github/` | PR 模板，标准化合并请求检查项 |

### 第四类：配置类文件 (Configuration)

| 文件 | 路径 | 说明 |
|------|------|------|
| `.editorconfig` | 根目录 | 统一不同编辑器的代码风格 |
| `.gitattributes` | 根目录 | Git 文件属性（换行符、语言统计等） |
| `CODEOWNERS` | `.github/` | 代码所有者，自动请求评审 |
| `dependabot.yml` | `.github/` | Dependabot 依赖自动更新配置 |

### 第五类：特定场景文件 (Special Scenarios)

| 文件 | 路径 | 适用场景 |
|------|------|------|
| `CITATION.cff` | 根目录 | 学术/科研项目，便于学术引用 |
| `NOTICE` | 根目录 | Apache-2.0 许可证或含第三方代码 |
| `AUTHORS` | 根目录 | 列出项目作者 |
| `MAINTAINERS.md` | 根目录 | 列出当前维护者 |
| `ARCHITECTURE.md` | 根目录 | 技术架构文档 |
| `ROADMAP.md` | 根目录 | 项目路线图 |
| `FAQ.md` | 根目录 | 常见问题解答 |
| `INSTALL.md` | 根目录 | 详细安装指南（当 README 安装部分过长时拆分） |
| `Dockerfile` | 根目录 | Docker 容器化部署 |
| `docker-compose.yml` | 根目录 | Docker Compose 多容器编排 |
| `.env.example` | 根目录 | 环境变量示例文件 |
| `Makefile` | 根目录 | 构建/测试自动化 |

---

## 决策矩阵

根据项目特征决定创建哪些文档。以下矩阵帮助做出判断：

### 必定创建（所有项目）

```
README.md + LICENSE + .gitignore
```

### 项目类型 → 推荐文档

| 项目特征 | 额外推荐文档 |
|----------|-------------|
| 接受外部贡献 | CONTRIBUTING.md + CODE_OF_CONDUCT.md + ISSUE_TEMPLATE/ + PULL_REQUEST_TEMPLATE.md |
| 有版本发布 | CHANGELOG.md |
| 处理敏感数据/有企业用户 | SECURITY.md |
| 用户量较大 | SUPPORT.md |
| 多人维护/大型项目 | GOVERNANCE.md + CODEOWNERS + MAINTAINERS.md |
| 学术/科研项目 | CITATION.cff |
| 使用 Apache-2.0 许可证 | NOTICE |
| 接受赞助 | FUNDING.yml |
| 有 Docker 部署需求 | Dockerfile + docker-compose.yml |
| 使用环境变量 | .env.example |
| 多人协作 | .editorconfig + .gitattributes |
| 跨平台项目 | .gitattributes |
| 文档量大 | docs/ 目录 + ARCHITECTURE.md |
| 常见问题多 | FAQ.md |
| 有明确路线图 | ROADMAP.md |
| 安装步骤复杂 | INSTALL.md |
| 有构建/测试流程 | Makefile |

### 技术栈 → .gitignore 模板

| 技术栈 | .gitignore 关键内容 |
|--------|---------------------|
| Node.js | `node_modules/`、`dist/`、`.env`、`npm-debug.log*` |
| Python | `__pycache__/`、`*.pyc`、`.venv/`、`*.egg-info/`、`.pytest_cache/` |
| Go | `*.exe`、`*.dll`、`*.so`、`*.dylib`、`vendor/`（视情况） |
| Rust | `target/`、`Cargo.lock`（库项目时） |
| Java | `target/`、`*.class`、`.gradle/`、`build/` |
| C# / .NET | `bin/`、`obj/`、`*.user`、`.vs/` |
| Godot | `.godot/`、`*.import`、`export_presets.cfg` |
| C/C++ | `*.o`、`*.obj`、`*.exe`、`*.a`、`*.so`、`build/` |

### 许可证选择指南

| 许可证 | 适用场景 | 特点 |
|--------|---------|------|
| MIT | 希望被广泛集成的库/工具 | 最宽松，几乎无限制 |
| Apache-2.0 | 企业级项目 | 明确专利授权，规避专利风险 |
| GPL-3.0 | 要求衍生作品也开源 | "传染性"开源，保护自由 |
| BSD-3-Clause | 学术/科研项目 | 类似 MIT，带广告条款 |
| LGPL-3.0 | 库/框架 | 允许非自由软件链接 |
| AGPL-3.0 | 网络服务 | 闭源网络服务也必须开源 |
| Unlicense | 完全放弃版权 | 公共领域 |

当用户未指定许可证时，默认推荐 MIT（通用）或 Apache-2.0（企业级）。最终选择应询问用户。

---

## 内容生成要点

生成文档时，遵循以下原则确保质量：

### README.md 生成要点

README 是最重要的文档。一个优秀的 README 应该让用户在 30 秒内理解"这是什么、能做什么、怎么用"。

必须包含的章节：
1. **项目标题 + 一句话描述** — 可选配 Badge（CI 状态、版本号、许可证）
2. **项目简介** — 解决什么问题，核心价值
3. **功能特性** — 列出关键功能点
4. **安装方式** — 具体命令（npm install、pip install、go get 等）
5. **快速开始** — 最小可用示例代码
6. **使用文档** — 或链接到详细文档
7. **配置说明** — 环境变量、配置文件等（如有）
8. **开发指南** — 链接到 CONTRIBUTING.md
9. **许可证** — 声明许可证并链接到 LICENSE 文件

可选章节（根据项目情况添加）：
- 项目截图/GIF 演示
- 架构图
- 常见问题（或链接到 FAQ.md）
- 贡献者列表
- 致谢
- 更新日志链接

### 其他文件生成要点

详细的每种文件内容指南，请阅读 `references/file-types-guide.md`。该文件包含：
- 每种文件的完整内容结构
- 模板和示例
- 最佳实践建议
- 常见错误避免

---

## 质量检查清单

生成文档后，逐项检查：

- [ ] README 是否能在 30 秒内让读者理解项目用途
- [ ] LICENSE 文件是否包含完整的许可证文本（不是仅有名称）
- [ ] .gitignore 是否覆盖了项目技术栈的常见忽略项
- [ ] 所有文档中的命令和路径是否与项目实际一致
- [ ] 文档之间的交叉链接是否正确
- [ ] 是否有占位符未填充（如 `TODO: 补充描述`）
- [ ] 代码示例是否可运行
- [ ] 文档语言是否与项目目标受众匹配
- [ ] Markdown 格式是否正确（标题层级、代码块语言标注等）

---

## 输出格式

最终向用户呈现：

1. **分析报告**：项目分析结果和选择的文档清单
2. **生成的文件**：每个文件的实际内容
3. **总结报告**：创建了哪些文件、建议补充的内容、未创建的文件及原因

在生成文件前，先向用户展示分析结果和建议创建的文件清单，征得确认后再开始生成。这样可以让用户在生成前调整选择。
