# Project Guidelines

## Scope

本仓库是 Copilot 插件发布与维护仓库，当前主插件为 `plugins/multi-role-delivery-workflow`（版本见 `plugins/multi-role-delivery-workflow/plugin.json`）。

## Architecture

- 根目录 `README.md`：插件索引与入口。
- `plugins/multi-role-delivery-workflow/agents/`：角色定义与 handoff。
- `plugins/multi-role-delivery-workflow/instructions/`：路由、上下文协议、文档输出规范。
- `plugins/multi-role-delivery-workflow/prompts/`：任务启动提示词。
- `plugins/multi-role-delivery-workflow/skills/`：技能入口（含 `0to1-delivery`）。
- `plugins/multi-role-delivery-workflow/hooks/`：安全、质量、完成三道门禁与脚本。

## Build And Test

本仓库当前没有统一的 package manager 脚本（无根级 `package.json`）。对插件规则变更，使用 Node 直接执行门禁脚本做回归检查：

```powershell
node plugins/multi-role-delivery-workflow/hooks/scripts/security-check.js
node plugins/multi-role-delivery-workflow/hooks/scripts/quality-check.js
node plugins/multi-role-delivery-workflow/hooks/scripts/completion-check.js
```

前提：Node.js 可用，建议版本 >= 20。

## Conventions

- 新增或修改插件资源时，遵循 `*.agent.md`、`*.instructions.md`、`*.prompt.md`、`hooks/*.json` 的现有命名与 frontmatter 结构。
- 不在工作区指令中重复复制详细规范；优先链接现有规范文档。
- 交付内容默认使用简体中文；必要术语可保留英文（如 API、CI/CD、MCP）。
- 修改工作流行为前，先核对 `CHANGELOG.md`，避免破坏已有兼容性。
- **文档同步规则**：每次修改插件内容（agents、instructions、prompts、hooks、skills、plugin.json）时，必须同步更新相应的文档：
  - 修改代理（agent）→ 更新 `plugins/multi-role-delivery-workflow/README.md` 的角色列表
  - 修改指令（instructions）→ 更新 `plugins/multi-role-delivery-workflow/CHANGELOG.md` 的工作流变更记录
  - 修改 plugin.json 版本或功能 → 更新 `plugins/multi-role-delivery-workflow/README.md` 和 `CHANGELOG.md`
  - 新增或修改技能（skills）→ 更新 `plugins/multi-role-delivery-workflow/README.md` 的技能索引

## Project-Specific Pitfalls

- 目录路径包含中文（例如工作区绝对路径），脚本与工具链需使用 UTF-8 并注意 Windows 编码差异。
- `hooks/*.json` 中命令路径指向 `.github/hooks/scripts/...`；在本仓库中实际脚本位于 `plugins/multi-role-delivery-workflow/hooks/scripts/`，验证时请使用真实路径。
- 安全门禁会拦截高危命令模式；自动化流程中应优先输出方案并标注待人工执行。

## Reference Docs

- 总体索引：`README.md`
- 插件说明：`plugins/multi-role-delivery-workflow/README.md`
- 版本变更：`plugins/multi-role-delivery-workflow/CHANGELOG.md`
- 工作流配置：`plugins/multi-role-delivery-workflow/instructions/workflow-config.instructions.md`
- 角色路由：`plugins/multi-role-delivery-workflow/instructions/role-routing.instructions.md`
- 上下文协议：`plugins/multi-role-delivery-workflow/instructions/agent-context-protocol.instructions.md`
- 文档输出规范：`plugins/multi-role-delivery-workflow/instructions/docs-output.instructions.md`
