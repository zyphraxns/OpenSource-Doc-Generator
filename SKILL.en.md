---
name: opensource-doc-generator
description: |
  Automatically generate the various documentation files required by open source platforms (such as GitHub) based on project files. It scans the project structure, code, and tech stack, intelligently determines which documentation files to create (README, LICENSE, CONTRIBUTING, CHANGELOG, CODE_OF_CONDUCT, SECURITY, and 20+ others), and generates spec-compliant content for each file.
  Whenever users mention intents such as "open source docs", "README", "upload to GitHub", "prepare for open source", "project description file", "doc generation", "open source preparation", "CONTRIBUTING", "LICENSE file", "CHANGELOG", etc., this Skill must be used. Even if the user simply says "write a description for my project" or "I want to open source my project", this Skill should be triggered.
---

# Open Source Documentation Generator

## Overview

This Skill helps Agents generate a complete, spec-compliant set of documentation for open source platforms (such as GitHub, GitLab, Gitee, etc.) based on a project's actual files and structure. The core approach is: **first analyze the project, then intelligently recommend tiered plans, and generate them one by one after user confirmation**.

The documentation quality of an open source project directly affects adoption rates, contributor growth, and community health. A good README lets users understand a project's value within 30 seconds; a clear CONTRIBUTING can cut the onboarding cost for contributors by 50%; and a project without a LICENSE is not legally open source at all.

## Workflow

### Step 1: Project Analysis

Scan the project in depth and collect the following information:

1. **Basic Project Information**
   - Project name (extracted from config files such as `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, `pom.xml`, `*.csproj`, etc.)
   - Project description and purpose
   - Version number
   - Author/maintainer information

2. **Tech Stack Identification**
   - Programming languages (inferred from file extensions and config files)
   - Frameworks and libraries (extracted from dependency files: `package.json`, `requirements.txt`, `Pipfile`, `go.sum`, `Cargo.lock`, etc.)
   - Build tools (Webpack, Vite, CMake, Makefile, Gradle, etc.)
   - Test frameworks (Jest, Pytest, Go test, etc.)
   - CI/CD configuration (whether `.github/workflows/`, `.gitlab-ci.yml`, etc. already exist)

3. **Project Structure Analysis**
   - Directory structure (distribution of source, docs, test, config directories, etc.)
   - Entry files (`main.py`, `index.js`, `src/main.rs`, `cmd/main.go`, etc.)
   - Documentation directories (`docs/`, `wiki/`, etc.)
   - Example code (`examples/`, `demo/`, etc.)

4. **Existing Documentation Check**
   - Check which documentation files already exist in the project root and the `.github/` directory
   - Check whether config files such as `.gitignore`, `.editorconfig` already exist
   - Check whether a LICENSE file already exists

5. **Project Characteristics Assessment**
   - Whether it is a library/framework (consumed by other projects)
   - Whether it is a standalone application/tool
   - Whether it is an academic/research project
   - Whether it has Docker support
   - Whether it has multi-language support
   - Project scale (small/medium/large)

### Step 2: Intelligent Tiered Recommendations

Based on the analysis results from Step 1, combined with the **Document Type Catalog** and **Decision Matrix** below, internally generate a set of tiered recommendation plans. This step does not need to output the full content to the user; instead, it prepares for the user interaction in Step 3.

The logic behind tiered recommendations is: different projects and different users have different needs for documentation completeness. Some want an exhaustive, full set of documents, while others only want the most basic files. Letting users choose via tiers respects their intent and avoids a one-size-fits-all approach.

### Step 3: User Confirmation & Selection

**This is the most critical interaction step.** Before actually generating files, you must present the analysis results and tiered recommendation plans to the user and let them make a choice. Never skip this step and generate files directly.

#### 3.1 Present the Project Analysis Summary

First, present the project analysis results to the user concisely, so the user can confirm whether the AI's understanding is correct:

```
## 项目分析摘要

- 项目名称：XXX
- 技术栈：Node.js / React / TypeScript
- 项目类型：独立应用
- 项目规模：小型
- 现有文档：已有 .gitignore，无其他文档
- 推测特征：接受外部贡献、有版本发布、跨平台
```

#### 3.2 Present the Tiered Recommendation Plans

Based on the project's characteristics, present 3-4 recommendation plans with varying levels of completeness. Each plan should include: a file list, a brief description, and applicable scenarios.

The recommended presentation format is as follows (using a Node.js project as an example):

```
## 推荐方案

根据你的项目特征，我准备了以下几套方案供你选择：

### 方案一：全套文档（最推荐）
适合希望长期维护、吸引社区贡献的正式开源项目。

包含文件：
- README.md — 项目说明，第一入口
- LICENSE — 开源许可证（需选择类型，见下方问题）
- .gitignore — Git 忽略规则
- CONTRIBUTING.md — 贡献指南
- CODE_OF_CONDUCT.md — 行为准则
- CHANGELOG.md — 变更日志
- .editorconfig — 编辑器风格统一
- .gitattributes — Git 文件属性
- .github/ISSUE_TEMPLATE/ — Issue 模板（Bug 报告 + 功能请求）
- .github/PULL_REQUEST_TEMPLATE.md — PR 模板

说明：这是最全面的方案，覆盖了开源项目所需的全部核心文档。
社区成员可以从 README 快速了解项目，通过 CONTRIBUTING 参与贡献，
通过 Issue/PR 模板高效沟通。适合面向公众、希望吸引贡献者的项目。

### 方案二：标准文档（推荐）
适合个人项目或小型团队，想要规范但不需要太多社区治理文件。

包含文件：
- README.md — 项目说明
- LICENSE — 开源许可证（需选择类型）
- .gitignore — Git 忽略规则
- CONTRIBUTING.md — 贡献指南
- CHANGELOG.md — 变更日志
- .editorconfig — 编辑器风格统一

说明：在必要文件基础上增加了贡献指南和变更日志，
适合有一定用户量但不强调社区治理的项目。

### 方案三：基础文档（精简）
适合快速开源、个人工具项目或原型阶段。

包含文件：
- README.md — 项目说明
- LICENSE — 开源许可证（需选择类型）
- .gitignore — Git 忽略规则

说明：只包含开源项目最基本的三件套。
能让别人看懂项目、合法使用代码、正确克隆仓库。
适合刚起步或仅供个人使用的项目。

### 方案四：仅 README（最小）
适合快速分享代码片段或实验性项目。

包含文件：
- README.md — 项目说明

说明：只有一个 README 文件，让别人能看懂项目做什么。
注意：没有 LICENSE 意味着他人在法律上无权使用你的代码。
仅适合实验性代码或内部演示。
```

The above is only an example. When actually recommending, adjust the specific file list of each plan based on the project's characteristics. For example:
- If the project has Docker deployment needs, Plan 1/2 should include `Dockerfile`
- If the project is an academic/research project, Plan 1/2 should include `CITATION.cff`
- If the project uses environment variables, Plan 1/2 should include `.env.example`
- If the project handles sensitive data, Plan 1 should include `SECURITY.md`

#### 3.3 Ask for Decisions the User Needs to Make

In addition to letting the user choose a plan, some file-specific details need user confirmation. These must be clarified before generation rather than guessed afterward.

**Must-ask items:**

1. **License type** (if the plan includes LICENSE and the project has not yet specified a license):
   ```
   LICENSE 文件需要选择许可证类型：
   - MIT：最宽松，几乎无限制，适合希望被广泛集成的项目（推荐）
   - Apache-2.0：明确专利授权，适合企业级项目
   - GPL-3.0：要求衍生作品也开源，保护自由
   - BSD-3-Clause：类似 MIT，适合学术/科研项目
   - 其他（请说明）
   
   你的项目使用哪种许可证？
   ```

2. **Documentation language** (if it cannot be clearly determined from project code comments and existing docs):
   ```
   文档使用什么语言？
   - 中文
   - 英文
   - 中英双语
   ```

3. **Author/copyright holder information** (if it cannot be extracted from config files):
   ```
   LICENSE 和 README 中需要填入作者/版权持有人名称，请提供：
   - 姓名/组织名：
   - 邮箱（可选）：
   - GitHub 用户名：
   ```

**Items that may need to be asked based on project characteristics:**

- If the project has Docker needs: Do you need a Dockerfile and docker-compose.yml generated?
- If the project is academic/research: Do you need a CITATION.cff generated? If so, what is the DOI?
- If the project accepts sponsorships: Do you need a FUNDING.yml generated? What is the sponsorship platform?
- If the project has CI/CD: Do you need a GitHub Actions workflow generated?

#### 3.4 Wait for the User's Reply

After presenting the above to the user, **stop and wait for the user's reply**. Do not assume the user's choices on your own.

Possible ways the user may reply:
- Select a plan (e.g., "I'll go with Plan 2")
- Add or remove files based on a plan (e.g., "Plan 1, but skip CODE_OF_CONDUCT")
- Answer the license, language, and other questions
- Make additional requests

After receiving the user's reply, finalize the list of files to create, then proceed to Step 4.

### Step 4: Document Generation

For each file type confirmed by the user:

1. Read the corresponding section in `references/file-types-guide.md` to understand the detailed content requirements and templates for that file
2. Combine the project information collected in Step 1 and the user-confirmed information in Step 3 to fill in the specific content
3. Generate the file at the correct path (root directory or `.github/` directory)
4. Perform a quality check on the generated content

Generation principles:
- Content should be **specific and accurate**, based on the project's actual code and configuration; avoid empty, templated language
- Use the project's actual commands, paths, and dependency names
- Keep the documentation language consistent with what the user confirmed in Step 3
- Keep cross-references between files consistent (e.g., references to LICENSE, CONTRIBUTING, etc. in README)
- If the user already has some files, **do not overwrite them**; instead, suggest the user refer to the generated version for improvements

### Step 5: Generate a Summary Report

After generating all files, output a summary report to the user, including:
- Which files were created and their paths
- A brief description of each file
- Suggested content to be added manually afterward (e.g., specific information that needs to be provided by the user)
- Files not created but potentially needed, and the reasons

---

## Document Type Catalog

The following lists all documentation files that may be needed, categorized by priority. For detailed content guidelines, read `references/file-types-guide.md`.

### Category 1: Required Files (Required)

| File | Path | Description |
|------|------|------|
| `README.md` | Root directory | The project's front door and primary entry point. Contains project intro, features, installation, usage examples, configuration, etc. |
| `LICENSE` | Root directory | Open source license. Code without a license is protected by copyright by default, and others have no right to use it. |
| `.gitignore` | Root directory | Git ignore rules, excluding build artifacts, dependencies, secrets, and other files that should not be committed. |

### Category 2: Strongly Recommended (Strongly Recommended)

| File | Path | Description |
|------|------|------|
| `CONTRIBUTING.md` | Root directory | Contribution guidelines, explaining how to submit Issues, PRs, set up dev environments, code standards, etc. |
| `CODE_OF_CONDUCT.md` | Root directory | Code of conduct, defining community participation standards and fostering a friendly collaboration environment. |
| `CHANGELOG.md` | Root directory | Changelog, recording additions, changes, fixes, removals, etc. by version. |

### Category 3: GitHub Community Health Files (Recommended)

| File | Path | Description |
|------|------|------|
| `SECURITY.md` | Root directory | Security policy, explaining how to report security vulnerabilities. |
| `SUPPORT.md` | Root directory | Support resources, telling users how to get help. |
| `FUNDING.yml` | `.github/` | Sponsorship config, displaying a Sponsor button on the repository. |
| `GOVERNANCE.md` | Root directory | Project governance, explaining role definitions and decision-making processes. |
| `ISSUE_TEMPLATE/` | `.github/` | Issue templates (bug reports, feature requests, etc.). |
| `PULL_REQUEST_TEMPLATE.md` | `.github/` | PR template, standardizing pull request checklists. |

### Category 4: Configuration Files (Configuration)

| File | Path | Description |
|------|------|------|
| `.editorconfig` | Root directory | Unifies code style across different editors. |
| `.gitattributes` | Root directory | Git file attributes (line endings, language stats, etc.). |
| `CODEOWNERS` | `.github/` | Code owners, automatically requesting reviews. |
| `dependabot.yml` | `.github/` | Dependabot dependency auto-update config. |

### Category 5: Special Scenario Files (Special Scenarios)

| File | Path | Applicable Scenario |
|------|------|------|
| `CITATION.cff` | Root directory | Academic/research projects, to facilitate academic citation. |
| `NOTICE` | Root directory | Apache-2.0 license or projects containing third-party code. |
| `AUTHORS` | Root directory | Lists project authors. |
| `MAINTAINERS.md` | Root directory | Lists current maintainers. |
| `ARCHITECTURE.md` | Root directory | Technical architecture documentation. |
| `ROADMAP.md` | Root directory | Project roadmap. |
| `FAQ.md` | Root directory | Frequently asked questions. |
| `INSTALL.md` | Root directory | Detailed installation guide (split out when the README installation section is too long). |
| `Dockerfile` | Root directory | Docker containerized deployment. |
| `docker-compose.yml` | Root directory | Docker Compose multi-container orchestration. |
| `.env.example` | Root directory | Environment variable example file. |
| `Makefile` | Root directory | Build/test automation. |

---

## Decision Matrix

The following matrix helps the Agent generate tiered recommendation plans in Step 2. Note: this is only an internal reference; which files are ultimately created is decided by the user in Step 3.

### Tiered Recommendation Plan Design Guide

When preparing recommendation plans for the user, follow these tiering principles:

**Plan 1 (Full Documentation)** should include:
- All required files + all strongly recommended files + all applicable community health files + all applicable configuration files + scenario files matching project characteristics

**Plan 2 (Standard Documentation)** should include:
- All required files + 2-3 of the strongly recommended files + 1-2 of the most relevant configuration files

**Plan 3 (Basic Documentation)** should include:
- All required files (README + LICENSE + .gitignore)

**Plan 4 (Minimal Documentation)** should include:
- Only README.md

Notes when designing plans:
- Every plan should include README.md; this is non-negotiable
- If the project already has certain files, mark them as "already exists" in the plan
- Scenario files (such as CITATION.cff, Dockerfile) should only be added to Plan 1 when they match project characteristics
- Do not put scenario files in Plan 3/4; keep them lean

### Project Characteristics → Recommended Documents

| Project Characteristic | Plan 1 Additionally Includes | Plan 2 Additionally Includes |
|----------|-------------|-------------|
| Accepts external contributions | ISSUE_TEMPLATE/ + PULL_REQUEST_TEMPLATE.md | CONTRIBUTING.md |
| Has version releases | CHANGELOG.md | CHANGELOG.md |
| Handles sensitive data / has enterprise users | SECURITY.md | — |
| Large user base | SUPPORT.md + SECURITY.md | — |
| Multi-maintainer / large project | GOVERNANCE.md + CODEOWNERS + MAINTAINERS.md | — |
| Academic/research project | CITATION.cff | — |
| Uses Apache-2.0 license | NOTICE | — |
| Accepts sponsorships | FUNDING.yml | — |
| Has Docker deployment needs | Dockerfile + docker-compose.yml | — |
| Uses environment variables | .env.example | — |
| Multi-person collaboration | .editorconfig + .gitattributes | .editorconfig |
| Cross-platform project | .gitattributes | — |
| Large documentation volume | ARCHITECTURE.md | — |
| Many common questions | FAQ.md | — |
| Has a clear roadmap | ROADMAP.md | — |
| Complex installation steps | INSTALL.md | — |
| Has build/test workflow | Makefile | — |

### Tech Stack → .gitignore Template

| Tech Stack | Key .gitignore Contents |
|--------|---------------------|
| Node.js | `node_modules/`, `dist/`, `.env`, `npm-debug.log*` |
| Python | `__pycache__/`, `*.pyc`, `.venv/`, `*.egg-info/`, `.pytest_cache/` |
| Go | `*.exe`, `*.dll`, `*.so`, `*.dylib`, `vendor/` (case by case) |
| Rust | `target/`, `Cargo.lock` (for library projects) |
| Java | `target/`, `*.class`, `.gradle/`, `build/` |
| C# / .NET | `bin/`, `obj/`, `*.user`, `.vs/` |
| Godot | `.godot/`, `*.import`, `export_presets.cfg` |
| C/C++ | `*.o`, `*.obj`, `*.exe`, `*.a`, `*.so`, `build/` |

### License Selection Guide

| License | Applicable Scenario | Characteristics |
|--------|---------|------|
| MIT | Libraries/tools that want broad adoption | Most permissive, almost no restrictions |
| Apache-2.0 | Enterprise-grade projects | Explicit patent grant, avoids patent risks |
| GPL-3.0 | Requires derivative works to be open source too | "Copyleft" open source, protects freedom |
| BSD-3-Clause | Academic/research projects | Similar to MIT, with advertising clause |
| LGPL-3.0 | Libraries/frameworks | Allows linking by non-free software |
| AGPL-3.0 | Network services | Closed-source network services must also be open source |
| Unlicense | Completely waives copyright | Public domain |

When the user has not specified a license, present the above options to the user in Step 3 and ask. Default recommendations are MIT (general purpose) or Apache-2.0 (enterprise-grade).

---

## Content Generation Key Points

When generating documents, follow these principles to ensure quality:

### README.md Generation Key Points

The README is the most important document. An excellent README should let users understand "what it is, what it can do, and how to use it" within 30 seconds.

Required sections:
1. **Project title + one-line description** — optionally with Badges (CI status, version, license)
2. **Project introduction** — what problem it solves, core value
3. **Features** — list key functionality
4. **Installation** — specific commands (npm install, pip install, go get, etc.)
5. **Quick start** — minimal working example code
6. **Usage documentation** — or link to detailed docs
7. **Configuration** — environment variables, config files, etc. (if any)
8. **Development guide** — link to CONTRIBUTING.md
9. **License** — declare the license and link to the LICENSE file

Optional sections (add as appropriate for the project):
- Project screenshots/GIF demos
- Architecture diagrams
- FAQ (or link to FAQ.md)
- Contributors list
- Acknowledgements
- Changelog link

### Other Files Generation Key Points

For detailed content guidelines for each file type, read `references/file-types-guide.md`. That file includes:
- The complete content structure for each file type
- Templates and examples
- Best practice recommendations
- Common mistakes to avoid

---

## Quality Checklist

After generating the documents, check each item:

- [ ] Can the README let readers understand the project's purpose within 30 seconds
- [ ] Does the LICENSE file contain the full license text (not just the name)
- [ ] Is the LICENSE file type consistent with what the user confirmed in Step 3
- [ ] Does the .gitignore cover the common ignore entries for the project's tech stack
- [ ] Are all commands and paths in the documentation consistent with the project's actual ones
- [ ] Are cross-links between documents correct
- [ ] Are there any unfilled placeholders (such as `TODO: add description`)
- [ ] Are code examples runnable
- [ ] Is the documentation language consistent with what the user confirmed in Step 3
- [ ] Is the Markdown formatting correct (heading hierarchy, code block language tags, etc.)
- [ ] Are the user's existing files left unoverwritten

---

## Output Format

Ultimately present to the user:

1. **Project Analysis Summary** (Step 3): a concise summary of project characteristics
2. **Tiered Recommendation Plans** (Step 3): 3-4 plans for the user to choose from
3. **Questions to Confirm** (Step 3): license type, documentation language, etc.
4. **Generated Files** (Step 4): the actual content of each file
5. **Summary Report** (Step 5): which files were created, suggested additions, files not created and the reasons
