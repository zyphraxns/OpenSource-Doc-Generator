# opensource-doc-generator

> A TRAE Work Skill that automatically generates all the documentation files your open-source project needs (README, LICENSE, CONTRIBUTING, and 20+ more) by analyzing your project structure, code, and tech stack.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![TRAE Work Skill](https://img.shields.io/badge/TRAE%20Work-Skill-blue.svg)](https://www.trae.cn/)

**[中文文档](README.md)**

## Overview

`opensource-doc-generator` is a [TRAE Work](https://www.trae.cn/) Skill that helps the AI agent generate a complete set of standardized documentation for open-source platforms (GitHub, GitLab, Gitee, etc.) based on your project's actual files and structure.

Core philosophy: **Analyze the project first, then present tiered recommendation plans, and generate only after user confirmation.**

Documentation quality directly impacts adoption rates, contributor growth, and community health. A good README lets users understand your project's value in 30 seconds. A clear CONTRIBUTING guide can cut contributor onboarding costs by 50%. And without a LICENSE file, your project isn't legally open source at all.

## Features

- **Intelligent Project Analysis** — Automatically scans project structure, config files, and tech stack to extract project name, version, dependencies, and more
- **20+ Document Types** — Covers README, LICENSE, CONTRIBUTING, CHANGELOG, CODE_OF_CONDUCT, SECURITY, Issue templates, PR templates, and all common open-source docs
- **Tiered Recommendation Plans** — Generates 3-4 plans at different completeness levels (Full / Standard / Basic / Minimal) tailored to your project, letting you choose
- **User Confirmation Mechanism** — Before generating anything, presents a project summary, tiered plans, and questions (license type, doc language, author info) for you to confirm
- **Decision Matrix Driven** — Recommends documents based on project characteristics (accepts contributions, has releases, handles sensitive data, etc.)
- **Tech Stack Aware** — Recognizes Node.js / Python / Go / Rust / Java / C# / Godot and generates appropriate .gitignore rules
- **License Selection Guide** — Built-in guidance for MIT / Apache-2.0 / GPL-3.0 / BSD / LGPL / AGPL with use-case descriptions
- **Detailed Content Guide** — Each document type has a complete content structure template and best practices (see `references/file-types-guide.en.md`)
- **Quality Checklist** — Post-generation checks for completeness, cross-reference consistency, unfilled placeholders, and more

## Installation

### Option 1: Manual Install

Clone this repo and copy the Skill files to your TRAE Work Skills directory:

```bash
git clone https://github.com/zyphraxns/opensource-doc-generator.git
cp opensource-doc-generator/SKILL.md ~/.trae-cn/skills/opensource-doc-generator/
cp -r opensource-doc-generator/references ~/.trae-cn/skills/opensource-doc-generator/
```

### Option 2: Direct Download

1. Download the ZIP of this repo
2. Copy `SKILL.md` and the `references/` folder into `~/.trae-cn/skills/opensource-doc-generator/`

The Skill will auto-load in your next TRAE Work session.

## Quick Start

After installation, just trigger it with natural language in TRAE Work:

```
Help me generate open-source docs for my project
```

Or more specifically:

```
I want to upload my project to GitHub, help me generate a README and other needed docs
```

The Skill will analyze your project, present recommendation plans for you to choose from, and generate the files after confirmation.

## Directory Structure

```
opensource-doc-generator/
├── SKILL.md                          # Skill main file (V2, Chinese)
├── SKILL.en.md                       # Skill main file (V2, English)
├── references/
│   ├── file-types-guide.md           # Detailed file type guide (Chinese)
│   └── file-types-guide.en.md        # Detailed file type guide (English)
├── V1/                               # First version (archived)
│   ├── SKILL.md
│   └── references/
│       └── file-types-guide.md
├── README.md                         # This file (Chinese)
├── README.en.md                      # English README
├── LICENSE                           # MIT License
├── CONTRIBUTING.md                   # Contribution guide
├── CODE_OF_CONDUCT.md               # Code of conduct
├── CHANGELOG.md                      # Changelog (bilingual)
├── .gitignore                        # Git ignore rules
├── .editorconfig                     # Editor config
├── .gitattributes                    # Git attributes
└── .github/
    ├── PULL_REQUEST_TEMPLATE.md     # PR template
    └── ISSUE_TEMPLATE/
        ├── bug_report.md            # Bug report template
        ├── feature_request.md       # Feature request template
        └── config.yml               # Issue template config
```

## Supported Document Types

| Category | File | Description |
|----------|------|-------------|
| **Required** | `README.md` | Project front door, first entry point |
| **Required** | `LICENSE` | Open-source license |
| **Required** | `.gitignore` | Git ignore rules |
| **Strongly Recommended** | `CONTRIBUTING.md` | Contribution guide |
| **Strongly Recommended** | `CODE_OF_CONDUCT.md` | Code of conduct |
| **Strongly Recommended** | `CHANGELOG.md` | Changelog |
| **Community Health** | `SECURITY.md` | Security policy |
| **Community Health** | `SUPPORT.md` | Support resources |
| **Community Health** | `FUNDING.yml` | Sponsor config |
| **Community Health** | `GOVERNANCE.md` | Project governance |
| **Community Health** | `ISSUE_TEMPLATE/` | Issue templates |
| **Community Health** | `PULL_REQUEST_TEMPLATE.md` | PR template |
| **Configuration** | `.editorconfig` | Editor style unification |
| **Configuration** | `.gitattributes` | Git file attributes |
| **Configuration** | `CODEOWNERS` | Code owners |
| **Configuration** | `dependabot.yml` | Dependency auto-update |
| **Scenario** | `CITATION.cff` | Academic citation |
| **Scenario** | `NOTICE` | Attribution notice |
| **Scenario** | `ARCHITECTURE.md` | Architecture doc |
| **Scenario** | `ROADMAP.md` | Roadmap |
| **Scenario** | `FAQ.md` | FAQ |
| **Scenario** | `INSTALL.md` | Install guide |
| **Scenario** | `Dockerfile` | Docker deployment |
| **Scenario** | `docker-compose.yml` | Docker orchestration |
| **Scenario** | `.env.example` | Env var example |
| **Scenario** | `Makefile` | Build automation |

## Workflow (V2)

The Skill executes five steps:

1. **Project Analysis** — Scans config files, tech stack, directory structure, existing docs
2. **Intelligent Tiered Recommendations** — Internally generates 3-4 recommendation plans at different completeness levels
3. **User Confirmation & Selection** — Presents project summary, tiered plans, and questions (license, language, author) — waits for your choice
4. **Document Generation** — Generates files based on your confirmed plan
5. **Summary Report** — Lists created files, suggestions, and files not created with reasons

## Version History

| Version | Description |
|---------|-------------|
| **V2** (current) | Adds user confirmation step: presents tiered recommendation plans before generating |
| V1 (archived in `V1/`) | Original: analyzes and generates directly without user confirmation |

## License

This project is licensed under the [MIT License](LICENSE).
