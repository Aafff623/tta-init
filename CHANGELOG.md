# Changelog

## 0.3.0 - 2026-09-02

- 重做为单 Project 初始化模型，彻底移除 Workspace + Project 设计。
- 将 `temp/` 定义为统一的本地临时工作区，覆盖调研、脚本、预览、报告、handoff、日志、缓存和本地密钥备份。
- 明确项目 Skills 可提交，MCP 配置、密钥和临时负载必须忽略。
- 以 Superpowers 作为开发工作流，以独立模板吸收 Matt Pocock 的治理资产思想。
- 增加 `README.md`、`AGENTS.md`、`CLAUDE.md`、`CONTEXT.md`、ADR、GitHub Issue/PR 模板。
- 删除空壳治理目录、虚构的跨工具 MCP 同步承诺和冗余生成目录设计。

## 历史版本

此前版本曾包含背景上下文轮、`CONTEXT-MAP` 和多端配置同步相关实验。它们不再代表当前 `tta-init` 的推荐模型；需要这些能力时，应基于当前单 Project 契约重新设计并经过实际工具验证。
