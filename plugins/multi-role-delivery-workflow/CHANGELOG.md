# Changelog

## 1.0.4 - 2026-04-17

- 新增工作流强制规则：每次写代码都必须写注释，复杂逻辑必须写详细注释。
- 增强 quality-gate：对常见代码文件增加“注释存在性”检查，不满足时阻断并要求修正。
- 增强 quality-gate：新增启发式复杂度校验（分支/循环/异常/并发等），复杂度高但注释密度或解释性不足时阻断。

## 1.0.3 - 2026-04-13

- 更新版本号为1.0.3，准备重新发布插件以解决在vs code显示multi-role-delivery-workflow:*.agent的问题。

## 1.0.2 - 2026-04-13

- 解决在vs code显示multi-role-delivery-workflow:*.agent的问题

## 1.0.1 - 2026-04-10

- 调整结构，解决在插件市场无法找到插件的问题

## 1.0.0 - 2026-04-03

- 首次插件化发布。
- 集成 agents/instructions/prompts/skills/hooks 全量能力。
- 内置 `.mcp.json`（filesystem/github/terminal）。
- 提供 completion-gate、quality-gate、security-gate 门禁能力。
