# Open Source Documentation File Types Detailed Guide

This file serves as a reference resource for the Skill, detailing the content structure, templates, and best practices for each type of documentation file. When generating specific files, the Agent should read the corresponding section for detailed guidance.

## Table of Contents

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
- [11. Issue Templates](#11-issue-templates)
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

**Path**: Repository root directory
**Importance**: Required — The most important project document, serving as the user's first impression

### Content Structure

```markdown
# Project Name

> A one-sentence description of what the project does

[![CI Status](badge-url)](ci-url)
[![License: MIT](badge-url)](license-url)
[![Version](badge-url)](version-url)

## Introduction

Explain in 2-3 paragraphs:
- What problem the project solves
- Why choose this project (core value/advantages)
- Use cases

## Features

- Feature 1: Brief description
- Feature 2: Brief description
- Feature 3: Brief description

## Installation

### Prerequisites

- Node.js >= 18 (or Python >= 3.10, etc. specific versions)
- Other system dependencies

### Installation Steps

\`\`\`bash
# Specific installation commands
npm install project-name
# or
pip install project-name
\`\`\`

## Quick Start

\`\`\`bash
# Minimal runnable example
\`\`\`

\`\`\`language
// Code example
\`\`\`

## Configuration

Explain configuration files, environment variables, etc. (if any):

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| PORT | number | 3000 | Service port |
| DATABASE_URL | string | - | Database connection URL |

## Documentation

- [Usage Documentation](docs/usage.md)
- [API Reference](docs/api.md)
- [FAQ](FAQ.md)

## Development

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for development environment setup and contribution process.

## Roadmap

See [ROADMAP.md](ROADMAP.md) for the project's future plans.

## Contributors

Thanks to everyone who has contributed to the project (you can use contrib.rocks to generate an image).

## License

This project is open-sourced under the [MIT](LICENSE) license.
```

### Best Practices

- The one-sentence description below the title should be concise and powerful, hitting the pain point directly
- Installation commands should be directly copy-paste runnable, including all prerequisite steps
- Quick Start examples should be as short as possible, allowing users to get running within 5 minutes
- Use badges to enhance visual appeal, but not too many (3-5 is ideal)
- If the project has a UI, add screenshots or GIF demos
- Keep the README concise, split detailed content into separate documents

---

## 2. LICENSE

**Path**: Repository root directory
**Importance**: Required — Code without a license is protected by copyright law by default, and others have no right to use it

### Content

The LICENSE file should contain the full license text, not just the license name. The full text of common licenses can be obtained from the following sources:

- MIT: https://choosealicense.com/licenses/mit/
- Apache-2.0: https://choosealicense.com/licenses/apache-2.0/
- GPL-3.0: https://choosealicense.com/licenses/gpl-3.0/
- BSD-3-Clause: https://choosealicense.com/licenses/bsd-3-clause/
- LGPL-3.0: https://choosealicense.com/licenses/lgpl-3.0/
- AGPL-3.0: https://choosealicense.com/licenses/agpl-3.0/

### Generation Guidelines

- MIT and BSD licenses require the year and copyright holder name to be filled in
- The Apache-2.0 license text requires a NOTICE file to be appended at the end (if the project uses Apache code)
- Do not modify the license text in any way, keep the original
- If the project uses dual licensing, explain in the LICENSE file and note it in the README

### Example (MIT)

```
MIT License

Copyright (c) [year] [copyright holder name]

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

**Path**: Repository root directory (can have multiple levels)
**Importance**: Required

### Content Structure

Based on the project's tech stack, ignore the following categories of files:

```gitignore
# Dependencies
node_modules/
.venv/
vendor/

# Build artifacts
dist/
build/
target/
*.class

# IDE configuration
.idea/
.vscode/
*.swp
*.swo
.DS_Store

# Environment variables and secrets
.env
.env.local
*.pem
*.key

# Logs
*.log
logs/

# OS files
Thumbs.db
.DS_Store

# Test coverage
coverage/
.nyc_output/
.pytest_cache/

# Cache
.cache/
__pycache__/
*.pyc
```

### Tech Stack Supplements

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

**Path**: Root directory (can also be in `.github/` or `docs/`)
**Importance**: Strongly recommended — GitHub automatically links this file when creating Issues/PRs

### Content Structure

```markdown
# Contributing Guidelines

Thank you for your interest in [Project Name]! This document will help you understand how to contribute to the project.

## Code of Conduct

By participating in this project, you agree to abide by the [Code of Conduct](CODE_OF_CONDUCT.md). Please be respectful and kind in all communications.

## How to Contribute

### Reporting Bugs

1. First search existing Issues to confirm the bug hasn't been reported
2. Create a new Issue using the Bug Report template
3. Provide the following information:
   - Operating system and version
   - Project version
   - Reproduction steps
   - Expected behavior and actual behavior
   - Error logs/screenshots

### Suggesting Features

1. First search existing Issues to confirm the suggestion hasn't been made
2. Create a new Issue using the Feature Request template
3. Explain:
   - The feature you want
   - Why you need this feature (use case)
   - Your expected implementation approach

### Submitting Code

#### Development Environment Setup

\`\`\`bash
# Clone the repository
git clone https://github.com/[org]/[repo].git
cd [repo]

# Install dependencies
npm install  # or pip install -e .[dev], etc.

# Run tests
npm test  # or pytest, etc.

# Start the development server
npm run dev  # or corresponding command
\`\`\`

#### Development Workflow

1. Fork the repository and create a branch:
   \`\`\`bash
   git checkout -b feat/your-feature-name
   \`\`\`
2. Write code, ensuring:
   - Code passes all tests: `npm test`
   - Code passes lint checks: `npm run lint`
   - New features have corresponding test cases
3. Commit code, following the Conventional Commits specification:
   \`\`\`
   feat: add user login feature
   fix: fix login page style issues
   docs: update README installation instructions
   refactor: refactor authentication module
   test: add test cases for login feature
   chore: upgrade dependency versions
   \`\`\`
4. Push and create a Pull Request

#### Branch Strategy

- `main`: Stable release branch
- `develop`: Development integration branch
- `feat/*`: New feature branches
- `fix/*`: Bug fix branches
- `hotfix/*`: Hotfix branches

#### Pull Request Requirements

- PR titles follow the Conventional Commits specification
- Provide a clear description of changes
- Link related Issues (e.g., `Closes #123`)
- Ensure CI checks pass
- If there are API changes, update corresponding documentation

## Code Standards

- Use [ESLint/Prettier/Black/gofmt, etc.] to format code
- Function/class/variable names should be semantic
- Add comments for complex logic
- New public APIs need JSDoc/docstring

## Project Structure

\`\`\`
project/
├── src/          # Source code
├── tests/        # Test files
├── docs/         # Documentation
├── examples/     # Examples
└── scripts/      # Scripts
\`\`\`

## Contact

If you have questions, you can contact maintainers through:
- GitHub Issues
- Email: [email]
- Community channel: [Discord/Slack link]
```

---

## 5. CODE_OF_CONDUCT.md

**Path**: Root directory
**Importance**: Strongly recommended — The foundation of community health

### Content Structure

Recommended to use the Contributor Covenant template (adopted by Kubernetes, Rails, Swift, and thousands of other projects):

```markdown
# Contributor Covenant

## Our Pledge

To foster an open and welcoming environment, as contributors and maintainers, we pledge to make participation in our project a harassment-free experience for everyone, regardless of age, body size, disability, ethnicity, sex characteristics, gender identity and expression, level of experience, education, socio-economic status, nationality, personal appearance, race, caste, color, religion, or sexual identity and orientation.

We pledge to act and interact in ways that contribute to an open, welcoming, diverse, inclusive, and healthy community.

## Our Standards

Examples of behavior that contributes to a positive environment:

* Demonstrating empathy and kindness toward others
* Respecting differing opinions, viewpoints, and experiences
* Giving and gracefully accepting constructive feedback
* Accepting responsibility, apologizing to those affected by our mistakes, and learning from the experience
* Focusing on what is best not just for us as individuals, but for the overall community

Examples of unacceptable behavior:

* The use of sexualized language or imagery, and sexual attention or advances of any kind
* Trolling, insulting or derogatory comments, and personal or political attacks
* Public or private harassment
* Publishing others' private information without explicit permission
* Other conduct which could reasonably be considered inappropriate in a professional setting

## Enforcement Responsibilities

Project maintainers are responsible for clarifying and enforcing our Code of Conduct and will take appropriate and fair corrective action in response to any behavior they deem inappropriate, threatening, offensive, or harmful.

## Scope

This Code of Conduct applies within all project spaces, and also applies when an individual is officially representing the project in public spaces.

## Enforcement

Instances of abusive, harassing, or otherwise unacceptable behavior may be reported to the project maintainers at [contact]. All complaints will be reviewed and investigated promptly and fairly.

## Attribution

This Code of Conduct is adapted from the [Contributor Covenant][homepage], version 2.1,
https://www.contributor-covenant.org/version/2/1/code_of_conduct.html

[homepage]: https://www.contributor-covenant.org
```

---

## 6. CHANGELOG.md

**Path**: Root directory
**Importance**: Strongly recommended — Follow the Keep a Changelog specification

### Content Structure

```markdown
# Changelog

All notable changes to this project are documented in this file.

Format based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

### Added
- New features pending release

## [1.0.0] - 2024-01-15

### Added
- Initial release
- Support for XXX feature
- Added YYY module

### Changed
- Refactored ZZZ module, improving performance by 30%

### Fixed
- Fixed crash in AAA scenario (#123)

### Deprecated
- BBB interface deprecated, will be removed in 2.0.0, use CCC as alternative

### Removed
- Removed DDD feature (deprecated since 0.9.0)

### Security
- Fixed CVE-2024-XXXX vulnerability

## [0.9.0] - 2023-10-01

### Added
- First beta version
```

### Change Category Description

| Category | Description |
|----------|-------------|
| Added | New features |
| Changed | Changes to existing functionality |
| Deprecated | Soon-to-be deprecated features |
| Removed | Removed features (typically previously Deprecated) |
| Fixed | Bug fixes |
| Security | Security-related fixes |

---

## 7. SECURITY.md

**Path**: Root directory (can also be in `.github/` or `docs/`)
**Importance**: Recommended — GitHub displays this file in the Security tab

### Content Structure

```markdown
# Security Policy

## Reporting Security Vulnerabilities

We take the security of our project seriously. If you discover a security vulnerability, please report it following these steps:

### Do Not Disclose Publicly

**Please do not report security vulnerabilities in GitHub Issues.**

### How to Report

1. Send an email to: [security@project.com]
2. Start the email subject with `[SECURITY]`
3. Provide the following information:
   - Vulnerability description
   - Reproduction steps
   - Impact scope
   - Suggested fix (if any)

### Encrypted Communication

If encrypted communication is needed, use the following PGP public key:
\`\`\`
-----BEGIN PGP PUBLIC KEY BLOCK-----
[PGP public key content]
-----END PGP PUBLIC KEY BLOCK-----
\`\`\`

## Response Time

| Stage | Time |
|-------|------|
| Confirm receipt of report | Within 48 hours |
| Initial assessment | Within 7 days |
| Fix solution | Within 30 days (critical vulnerabilities prioritized) |
| Patch release | Within 7 days after fix is completed |

## Supported Versions

| Version | Support Status |
|---------|----------------|
| 1.x | :white_check_mark: Security updates |
| 0.x | :x: No longer supported |

## Security Best Practices

- Always use the latest version
- Do not hardcode secrets in code
- Use environment variables to manage sensitive configuration
- Regularly update dependencies
```

---

## 8. SUPPORT.md

**Path**: Root directory (can also be in `.github/` or `docs/`)
**Importance**: Recommended

### Content Structure

```markdown
# Getting Help

Before seeking help, please check the following resources:

## Documentation

- [README](README.md) — Project overview and quick start
- [Usage Documentation](docs/) — Detailed usage instructions
- [API Reference](docs/api.md) — API documentation
- [FAQ](FAQ.md) — Frequently asked questions

## Asking Questions

If you encounter a problem:

1. **Search first**: Search [GitHub Issues](issues-url) to see if anyone has encountered the same problem
2. **File an Issue**: If you can't find a solution, create a new Issue
   - Use the Issue template
   - Provide detailed problem description, reproduction steps, and environment info
3. **Discussions**: For usage questions rather than bugs, discuss in [GitHub Discussions](discussions-url)

## Community

- **Discord/Slack**: [Join link]
- **Stack Overflow**: Ask questions using the `[project-name]` tag

## Commercial Support

For commercial support, please contact: [email]

## Issues Not to Report Here

Please do not report the following through Issues:

- Security vulnerabilities → Please read [SECURITY.md](SECURITY.md)
- Feature suggestions → Please use the Feature Request template
- Usage questions → Please discuss in Discussions
```

---

## 9. FUNDING.yml

**Path**: `.github/FUNDING.yml`
**Importance**: Optional — Displays a Sponsor button on the repository

### Content Structure

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

# Custom links (up to 4)
custom: ["https://example.com/donate", "https://example.com/wishlist"]
```

### Notes

Only fill in the sponsorship platforms you actually use; you don't need to fill in all of them.

---

## 10. GOVERNANCE.md

**Path**: Root directory
**Importance**: Recommended — Suitable for medium to large projects with multiple maintainers

### Content Structure

```markdown
# Project Governance

## Roles

### Contributor

Anyone who has submitted and merged a PR is a contributor. Contributor rights:
- Submit Issues and PRs
- Participate in design discussions
- Review others' PRs

### Committer

Members with write access to the repository. Requirements:
- Consistently contributing high-quality code for 3+ months
- Recommended by 2+ maintainers
- Familiar with project code standards and architecture

Committer rights:
- All contributor rights
- Merge PRs
- Create branches and tags

### Maintainer

Members with administrative access to the repository. Requirements:
- Served as committer for 6+ months
- Recommended by 2+ maintainers
- Demonstrated understanding and judgment of project direction

Maintainer rights:
- All committer rights
- Release versions
- Manage Issue and PR labels
- Participate in project roadmap decisions

## Decision-Making Process

### Small-Scope Decisions

Discussed and decided by the committers/maintainers of the relevant module.

### Large-Scope Decisions

Major decisions affecting project direction (e.g., architecture changes, license changes, etc.):
1. Submit an RFC (Request for Comments)
2. Community discussion (at least 2 weeks)
3. Maintainer vote (simple majority to pass)
4. Announce decision results

### Voting Mechanism

- +1: In favor
- 0: Neutral
- -1: Against (reason required)
- Decisions require a simple majority (>50%) of votes in favor

## Promotion and Demotion

- Promotion: Nominated and voted by existing maintainers after meeting requirements
- Demotion: Inactive committers/maintainers (6+ months) will be converted to emeritus members
```

---

## 11. Issue Templates

**Path**: `.github/ISSUE_TEMPLATE/`
**Importance**: Recommended

### Bug Report Template (`.github/ISSUE_TEMPLATE/bug_report.md`)

```markdown
---
name: Bug Report
about: Report a bug to help us improve
title: '[BUG] '
labels: bug
assignees: ''
---

## Bug Description

Briefly describe the problem you encountered.

## Reproduction Steps

1. Go to '...'
2. Click on '...'
3. Scroll to '...'
4. See error

## Expected Behavior

Describe what you expected to happen.

## Actual Behavior

Describe what actually happened.

## Environment

- OS: [e.g., macOS 14.0, Ubuntu 22.04]
- Project version: [e.g., 1.2.3]
- Runtime version: [e.g., Node.js 18.17.0, Python 3.11.4]
- Browser (if applicable): [e.g., Chrome 120]

## Screenshots/Logs

If you have screenshots or error logs, please attach them.

## Additional Information

Any other information that might help diagnose the problem.
```

### Feature Request Template (`.github/ISSUE_TEMPLATE/feature_request.md`)

```markdown
---
name: Feature Request
about: Suggest a new feature or improvement
title: '[FEATURE] '
labels: enhancement
assignees: ''
---

## Feature Description

Briefly describe the feature you'd like to see added.

## Problem to Solve

What problem does this feature solve? (e.g., "Every time I need to do X, it's inconvenient because...")

## Proposed Solution

Describe the solution you'd like.

## Alternative Solutions

Other solutions you've considered.

## Additional Information

Any other relevant screenshots, links, or information.
```

### Issue Template Configuration (`.github/ISSUE_TEMPLATE/config.yml`)

```yaml
blank_issues_enabled: false
contact_links:
  - name: Usage Questions
    url: https://github.com/org/repo/discussions
    about: Please discuss usage questions in Discussions
  - name: Security Vulnerability
    url: https://github.com/org/repo/security/policy
    about: Please see the security policy for vulnerability reports
```

---

## 12. PULL_REQUEST_TEMPLATE.md

**Path**: `.github/PULL_REQUEST_TEMPLATE.md`
**Importance**: Recommended

### Content Structure

```markdown
## Description of Changes

Briefly describe what changes this PR makes.

## Change Type

- [ ] Bug fix (fix)
- [ ] New feature (feat)
- [ ] Breaking change (BREAKING CHANGE)
- [ ] Documentation update (docs)
- [ ] Refactor (refactor)
- [ ] Performance improvement (perf)
- [ ] Test (test)
- [ ] Build/CI (chore)

## Related Issue

Closes #(issue number)

## Checklist

- [ ] Code passes lint checks
- [ ] Code passes all tests
- [ ] New features have corresponding test cases
- [ ] Documentation has been updated (if needed)
- [ ] Commit messages follow Conventional Commits specification
- [ ] No new warnings introduced

## Screenshots/Demo

If there are UI changes, please attach screenshots or screen recordings.

## Breaking Changes

If this PR includes breaking changes, please describe:
- What changed
- Migration guide
- Impact scope
```

---

## 13. .editorconfig

**Path**: Root directory
**Importance**: Recommended — Ensures consistent coding styles in multi-person collaboration

### Content Structure

```ini
# EditorConfig: https://editorconfig.org
# Helps maintain consistent coding styles across different editors/IDEs

root = true

# All files
[*]
charset = utf-8
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true
indent_style = space
indent_size = 2

# Python files
[*.py]
indent_size = 4

# Go files
[*.go]
indent_style = tab

# Markdown files (preserve trailing whitespace)
[*.md]
trim_trailing_whitespace = false

# Makefile (must use tab)
[Makefile]
indent_style = tab

# YAML files
[*.{yml,yaml}]
indent_size = 2

# JSON files
[*.json]
indent_size = 2
```

---

## 14. .gitattributes

**Path**: Root directory
**Importance**: Recommended — Cross-platform collaboration and language statistics correction

### Content Structure

```gitattributes
# Unify line endings
* text=auto eol=lf

# Specific file types
*.bat text eol=crlf
*.sh text eol=lf
*.ps1 text eol=crlf

# Binary files
*.png binary
*.jpg binary
*.gif binary
*.ico binary
*.pdf binary
*.zip binary

# Language statistics correction (exclude certain files from language stats)
docs/* linguist-documentation
*.min.js linguist-generated
*.lock linguist-generated

# Export ignore (not included in git archive)
.gitattributes export-ignore
.gitignore export-ignore
.github export-ignore
tests export-ignore
```

---

## 15. CODEOWNERS

**Path**: `.github/CODEOWNERS` (can also be in root directory)
**Importance**: Recommended — GitHub automatically requests code owner reviews

### Content Structure

```gitowners
# Format: file path pattern @username @team

# Default owners
* @maintainer1 @maintainer2

# Frontend code
/src/frontend/ @frontend-team @maintainer1

# Backend code
/src/backend/ @backend-team @maintainer2

# Infrastructure
/.github/ @devops-team
/Dockerfile @devops-team
/docker-compose.yml @devops-team

# Documentation
/docs/ @docs-team @maintainer1
*.md @docs-team

# Tests
/tests/ @qa-team
```

---

## 16. dependabot.yml

**Path**: `.github/dependabot.yml`
**Importance**: Optional — Automated dependency updates

### Content Structure

```yaml
version: 2
updates:
  # npm dependencies
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

  # pip dependencies
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

  # Docker base images
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

**Path**: Root directory
**Importance**: Specific scenarios — Academic/research projects

### Content Structure

```yaml
cff-version: 1.2.0
message: "If you use this project, please cite it using the format below."
title: "Project Name"
authors:
  - given-names: "First name"
    family-names: "Last name"
    orcid: "https://orcid.org/0000-0000-0000-0000"
    affiliation: "Affiliation"
version: "1.0.0"
date-released: "2024-01-15"
doi: "10.5281/zenodo.xxxxxxx"
license: "MIT"
repository-code: "https://github.com/org/repo"
url: "https://project-website.com"
keywords:
  - "keyword1"
  - "keyword2"
preferred-citation:
  type: "software"
  authors:
    - given-names: "First name"
      family-names: "Last name"
  title: "Project Name"
  year: 2024
```

---

## 18. NOTICE

**Path**: Root directory
**Importance**: Specific scenarios — Apache-2.0 license or projects including third-party code

### Content Structure

```
Project Name
Copyright 2024 [copyright holder]

This product includes software developed by the Apache Software Foundation
(https://www.apache.org/).

This product includes the following third-party components:

1. Component Name
   Copyright [year] [author]
   License: [license name]
   URL: [project URL]

2. Another Component
   Copyright [year] [author]
   License: [license name]
```

---

## 19. AUTHORS / MAINTAINERS.md

**Path**: Root directory
**Importance**: Optional

### AUTHORS

```
# Alphabetical order

John Doe <john@example.com>
Jane Smith <jane@example.com>
Zhang San <zhangsan@example.com>
```

### MAINTAINERS.md

```markdown
# Maintainers

## Current Maintainers

| Name | Role | GitHub |
|------|------|--------|
| Zhang San | Project Lead | @zhangsan |
| Li Si | Core Maintainer | @lisi |
| Wang Wu | Maintainer | @wangwu |

## Emeritus Maintainers

| Name | Contribution | GitHub |
|------|-------------|--------|
| Zhao Liu | Former Core Maintainer | @zhaoliu |

## Contact

- Security issues: security@project.com
- General questions: via GitHub Issues
```

---

## 20. ARCHITECTURE.md

**Path**: Root directory
**Importance**: Specific scenarios — Medium to large projects

### Content Structure

```markdown
# Architecture Design

## Overview

[Project Name] adopts a [architecture style] architecture, divided into the following modules:

## System Architecture Diagram

\`\`\`
┌────────────┐    ┌────────────┐    ┌────────────┐
│ Frontend UI│───→│  API Layer │───→│Data Storage│
└────────────┘    └────────────┘    └────────────┘
                      │
                      ↓
                ┌────────────┐
                │ Task Queue │
                └────────────┘
\`\`\`

## Module Description

### Frontend (frontend/)
- Tech stack: [framework]
- Responsibilities: User interface rendering, interaction handling

### API Layer (api/)
- Tech stack: [framework]
- Responsibilities: Request routing, business logic, data validation

### Data Layer (data/)
- Tech stack: [database]
- Responsibilities: Data persistence, caching

## Data Flow

1. User initiates a request through the frontend
2. API layer receives the request, performs authentication and parameter validation
3. After business logic processing, reads/writes to the data layer
4. Asynchronous tasks enter the task queue
5. Returns response to the frontend

## Design Decisions

### Why [technology] instead of [alternative]?

[Decision rationale and trade-offs]

### Why [architecture pattern]?

[Decision rationale and trade-offs]

## Scalability Considerations

- [How to scale horizontally]
- [How to add new modules]
- [Data sharding strategy]
```

---

## 21. ROADMAP.md

**Path**: Root directory
**Importance**: Optional

### Content Structure

```markdown
# Project Roadmap

## Current Version: v1.0.0 (2024 Q1)

- [x] Core feature A
- [x] Core feature B
- [x] Basic documentation and tests

## Next Version: v1.1.0 (2024 Q2)

- [ ] Performance optimization
- [ ] Feature C
- [ ] Plugin system

## Future Plans

### v2.0.0 (2024 Q4)
- [ ] Architecture refactoring
- [ ] Feature D
- [ ] Multi-language support

### Exploring
- [ ] Feature E
- [ ] F integration

## Version Planning Principles

- Follow Semantic Versioning (SemVer)
- Minor versions released every [cycle]
- Major versions determined by project progress
- Roadmap may be adjusted based on community feedback
```

---

## 22. FAQ.md

**Path**: Root directory
**Importance**: Optional

### Content Structure

```markdown
# FAQ

## Installation

### Q: What should I do if I get `error: XXX` during installation?

A: This is usually because [reason]. Please try:
1. Check if Node.js version is >= 18
2. Clear cache: `npm cache clean --force`
3. Reinstall: `rm -rf node_modules && npm install`

### Q: Is Windows supported?

A: Yes. However, WSL2 is recommended for the best experience.

## Usage

### Q: How to customize the XXX configuration?

A: Set the `xxx` option in the configuration file:
\`\`\`yaml
xxx:
  enabled: true
  value: "custom"
\`\`\`

### Q: Where is data stored?

A: By default, data is stored in the `~/.project/data/` directory, which can be changed via the `DATA_DIR` environment variable.

## Development

### Q: How to run tests?

A: \`\`\`bash
npm test          # Run all tests
npm run test:unit # Unit tests
npm run test:e2e  # End-to-end tests
\`\`\`

### Q: How to add a new feature?

A: Please read [CONTRIBUTING.md](CONTRIBUTING.md) for the development workflow.

## Other

### Q: What's the difference between this project and similar projects?

A: [Brief explanation of differentiating advantages]

### Q: Is there a commercial version?

A: [Explain business model or state there is no commercial version]
```

---

## 23. INSTALL.md

**Path**: Root directory
**Importance**: Specific scenarios — Split out when the installation section in README is too long

### Content Structure

```markdown
# Installation Guide

## System Requirements

| Requirement | Minimum | Recommended |
|-------------|---------|-------------|
| OS | macOS 12 / Ubuntu 20.04 / Windows 10 | Latest version |
| Runtime | Node.js 18 | Node.js 20 LTS |
| Memory | 512MB | 2GB+ |
| Disk | 100MB | 1GB+ |

## Installation Methods

### Method 1: Package Manager (Recommended)

\`\`\`bash
# npm
npm install -g project-name

# yarn
yarn global add project-name

# pnpm
pnpm add -g project-name
\`\`\`

### Method 2: Build from Source

\`\`\`bash
# Clone the repository
git clone https://github.com/org/repo.git
cd repo

# Install dependencies
npm install

# Build
npm run build

# Global link
npm link
\`\`\`

### Method 3: Docker

\`\`\`bash
docker pull org/project-name:latest
docker run -d -p 3000:3000 org/project-name
\`\`\`

## Verify Installation

\`\`\`bash
project-name --version
\`\`\`

If the version number is output, the installation was successful.

## Platform-Specific Notes

### macOS

Install using Homebrew:
\`\`\`bash
brew install project-name
\`\`\`

### Linux

\`\`\`bash
# Download binary
curl -L https://github.com/org/repo/releases/latest/download/project-linux-amd64 -o /usr/local/bin/project-name
chmod +x /usr/local/bin/project-name
\`\`\`

### Windows

Download the `.exe` installer from [Releases](releases-url).

## Uninstall

\`\`\`bash
npm uninstall -g project-name
\`\`\`

## Troubleshooting

### Permission Error (EACCES)

\`\`\`bash
# Option 1: Use nvm to manage Node.js
# Option 2: Change npm global install directory
npm config set prefix ~/.npm-global
export PATH=~/.npm-global/bin:$PATH
\`\`\`

### Network Timeout

\`\`\`bash
# Use mirror registry
npm install -g project-name --registry=https://registry.npmmirror.com
\`\`\`
```

---

## 24. Dockerfile

**Path**: Root directory
**Importance**: Specific scenarios

### Content Structure (Multi-stage build example)

```dockerfile
# Build stage
FROM node:20-alpine AS builder

WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm ci

# Copy source code and build
COPY . .
RUN npm run build

# Runtime stage
FROM node:20-alpine AS runner

WORKDIR /app

ENV NODE_ENV=production

# Only copy necessary files
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package.json ./

# Expose port
EXPOSE 3000

# Health check
HEALTHCHECK --interval=30s --timeout=3s --retries=3 \
  CMD wget --no-verbose --tries=1 --spider http://localhost:3000/health || exit 1

# Run as non-root user
USER node

CMD ["node", "dist/index.js"]
```

### Generation Guidelines

- Use multi-stage builds to reduce image size
- Use Alpine base image
- Run as non-root user
- Add HEALTHCHECK
- Leverage Docker layer caching effectively (COPY dependency files first, then source code)
- Adjust according to the project's actual tech stack

---

## 25. docker-compose.yml

**Path**: Root directory
**Importance**: Specific scenarios

### Content Structure

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

**Path**: Root directory
**Importance**: Specific scenarios — When the project uses environment variables

### Content Structure

```bash
# Server configuration
PORT=3000
HOST=0.0.0.0
NODE_ENV=development

# Database
DATABASE_URL=postgresql://user:password@localhost:5432/dbname

# Redis
REDIS_URL=redis://localhost:6379

# Authentication
JWT_SECRET=your-jwt-secret-here
JWT_EXPIRES_IN=7d

# Third-party services
SMTP_HOST=smtp.example.com
SMTP_PORT=587
SMTP_USER=your-email@example.com
SMTP_PASS=your-email-password

# API keys (example only, do not use real keys)
API_KEY=your-api-key-here

# Logging
LOG_LEVEL=debug
```

### Generation Guidelines

- Include all environment variables required by the project
- Use example values, do not use real secrets
- Group by function and add comments
- Ensure .env is ignored in .gitignore

---

## 27. Makefile

**Path**: Root directory
**Importance**: Specific scenarios — Projects with build/test workflows

### Content Structure

```makefile
.PHONY: install dev build test lint clean docker-build docker-up docker-down help

# Default target
.DEFAULT_GOAL := help

# Variables
VERSION := $(shell git describe --tags --always --dirty 2>/dev/null || echo "dev")
DOCKER_IMAGE := project-name

help: ## Show help information
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | \
		awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-20s\033[0m %s\n", $$1, $$2}'

install: ## Install dependencies
	npm install

dev: ## Start development server
	npm run dev

build: ## Build project
	npm run build

test: ## Run tests
	npm test

test-coverage: ## Run tests and generate coverage report
	npm run test:coverage

lint: ## Code linting
	npm run lint

lint-fix: ## Auto-fix code style
	npm run lint:fix

clean: ## Clean build artifacts
	rm -rf dist node_modules/.cache

docker-build: ## Build Docker image
	docker build -t $(DOCKER_IMAGE):$(VERSION) .

docker-up: ## Start Docker containers
	docker compose up -d

docker-down: ## Stop Docker containers
	docker compose down

release: ## Release new version
	@echo "Current version: $(VERSION)"
	@read -p "Enter new version number: " new_version; \
	git tag -a v$$new_version -m "Release v$$new_version"; \
	git push origin v$$new_version
```

### Generation Guidelines

- Always include a `help` target
- Use `.PHONY` to declare non-file targets
- Commands should match the project's actual build/test commands
- Target names should be semantic
```
