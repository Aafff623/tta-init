# tta-init

`tta-init` 是一个面向 AI 辅助开发项目的初始化 Skill。它采用单 Project 模式，帮助 Agent 建立清晰的规则入口、项目上下文、`temp/` 本地工作区，以及可选的 GitHub Issue/PR 模板。

## 设计边界

- Superpowers 负责实际开发工作流：澄清、规划、实现、测试、评审和验证。
- Matt Pocock 方法论只被重新编写为少量治理资产模板，不安装或复制 Matt 的 Skills 包。
- 项目 Skills 是可提交的项目资产；MCP 配置、密钥和 `temp/` 负载是本地运行资产，默认忽略。
- 不创建 Workspace + Project 双层结构，不创建空的 `.agents/generated/`，也不声称存在未经验证的 `tta mcp sync` 命令。

## Skill package

实际 Skill 位于 [`skills/tta-init/`](skills/tta-init/)。其中：

- `SKILL.md` 定义触发条件、初始化流程和安全边界；
- `references/` 保存文件树、MCP 和治理资产契约；
- `assets/templates/` 保存项目与 GitHub 的可渲染模板；
- `agents/openai.yaml` 提供 Codex 的展示信息和默认提示词。

## 初始化后的核心形状

```text
project/
├── README.md
├── AGENTS.md
├── CLAUDE.md
├── CONTEXT.md
├── .gitignore
├── .agents/skills/       # 有实际项目 Skill 时保留并提交
└── temp/                 # 负载忽略，仅保留规则入口
    ├── README.md
    └── AGENTS.md
```

ADR、GitHub Issue/PR 模板、长期脚本和核心图片资产按需添加，不为了填满目录而生成空文件。

## 安装与使用

将 `skills/tta-init/` 放入当前 AI 编程工具支持的 Skills 目录，然后在目标 Project 根目录调用 `tta-init`。不同工具的安装目录和 MCP 入口并不统一；本仓库不会伪装出一个跨工具自动同步器。

初始化前，Skill 会检查现有规则、Git 状态、未提交工作和已有配置；初始化后会报告新增、保留、跳过和未验证的内容。
