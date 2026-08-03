# 贡献指南

感谢你对 opensource-doc-generator 的关注！本文档将帮助你了解如何参与项目贡献。

## 行为准则

参与本项目即代表你同意遵守 [行为准则](CODE_OF_CONDUCT.md)。请在所有交流中保持尊重和友善。

## 如何贡献

### 报告 Bug

1. 先搜索现有 [Issues](https://github.com/zyphraxns/opensource-doc-generator/issues)，确认该 Bug 未被报告过
2. 使用 Bug 报告模板创建新 Issue
3. 提供以下信息：
   - 操作系统和版本
   - TRAE Work 版本
   - 复现步骤
   - 预期行为和实际行为
   - 错误日志/截图

### 提出功能建议

1. 先搜索现有 Issues，确认该建议未被提出过
2. 使用功能请求模板创建新 Issue
3. 说明：
   - 你想要的功能
   - 为什么需要这个功能（使用场景）
   - 你期望的实现方式

### 提交代码

#### 开发环境配置

本项目是纯 Markdown 文档项目，无需安装依赖。只需克隆仓库即可开始编辑：

```bash
git clone https://github.com/zyphraxns/opensource-doc-generator.git
cd opensource-doc-generator
```

#### 开发流程

1. Fork 仓库并创建分支：
   ```bash
   git checkout -b feat/your-feature-name
   ```
2. 编辑文件，确保：
   - Markdown 格式正确（标题层级、代码块语言标注等）
   - 内容具体准确，不使用空洞的模板化语言
   - 文件之间的交叉引用保持一致
3. 提交代码，遵循 Conventional Commits 规范：
   ```
   feat: 添加 XXX 文档类型支持
   fix: 修复 XXX 模板中的错误
   docs: 更新 README 安装说明
   refactor: 重构决策矩阵逻辑
   ```
4. 推送并创建 Pull Request

#### Pull Request 要求

- PR 标题遵循 Conventional Commits 规范
- 提供清晰的变更说明
- 关联相关 Issue（如 `Closes #123`）
- 如果修改了 SKILL.md 的工作流程，说明变更原因

## 文档规范

### Markdown 格式

- 使用 ATX 风格标题（`#` 而非下划线）
- 代码块必须标注语言（```bash、```yaml 等）
- 表格使用标准 Markdown 表格语法
- 列表使用 `-` 而非 `*`

### 内容原则

- 内容要具体且准确，基于实际场景
- 使用清晰的中文表达（本项目以中文为主）
- 避免使用 `TODO` 或占位符
- 保持文档之间的交叉引用一致

## 项目结构

```
opensource-doc-generator/
├── SKILL.md                    # Skill 主文件
├── references/
│   └── file-types-guide.md     # 详细文件类型指南
└── .github/                    # GitHub 配置和模板
```

### 修改 SKILL.md

SKILL.md 是 Skill 的核心文件，修改时注意：
- 保持 YAML frontmatter 格式正确
- description 字段是触发机制的关键，修改时确保触发词覆盖全面
- 工作流程的四个步骤顺序不要随意调整

### 修改 references/file-types-guide.md

这是详细的文件类型指南，修改时注意：
- 每种文件类型的章节结构保持一致
- 模板中的示例要可运行
- 新增文件类型时，同步更新 SKILL.md 中的文档类型目录

## 联系方式

如有疑问，可以通过以下方式联系维护者：
- GitHub [Issues](https://github.com/zyphraxns/opensource-doc-generator/issues)
- 邮箱：ziliang.qui@this-weimar.com
