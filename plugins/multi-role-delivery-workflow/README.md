# multi-role-delivery-workflow

## 1. 插件说明

这是将全角色项目交付工作流插件化后的可复用包，目标是让多个仓库快速复用同一套多角色协作交付流程。

包含组件：

- `agents/`：角色定义与 handoff 路由
- `instructions/`：路由、协议和输出规范
- `prompts/`：`/refactor`、`/test-automation`、`/doc-generation`
- `skills/`：`0to1-delivery` 技能入口
- `hooks/`：security/quality/completion 三道门禁及脚本
- `.mcp.json`：filesystem/github/terminal MCP 服务器配置
- `copilot-instructions.md`：全局工作区协作指令

## 2. 使用方式

1. 将本目录发布到你们的 Plugin Registry（或内部分发仓库）。
2. 在 VS Code 设置中配置 `chat.plugins.marketplaces`。
3. 在 Chat 插件管理中启用 `multi-role-delivery-workflow`。
4. 在项目中调用 `0to1-delivery` 或单阶段命令开始协作。

## 3. 最佳实践

- 最小权限：仅保留任务必需工具，避免过度授权。
- 本地优先：当插件规则与项目本地规则冲突时，以本地 `.github/instructions` 和 `.github/hooks` 为准。
- 版本治理：采用语义化版本（`MAJOR.MINOR.PATCH`），每次发布记录变更。
- 安全合规：`GITHUB_TOKEN` 仅走环境变量，禁止明文写入。
- 渐进推广：先在 1-2 个试点仓验证，再扩大到团队范围。

## 4. 升级与兼容

- 升级前先看 `CHANGELOG.md`，确认是否存在破坏性变更。
- 对于 `hooks/` 规则变更，建议先在测试仓验证。
- 对于 `agents/` handoff 变更，建议回归 0to1 主流程一次。

## 5. 目录结构

```text
multi-role-delivery-workflow/
├── plugin.json
├── README.md
├── CHANGELOG.md
├── copilot-instructions.md
├── agents/
├── instructions/
├── prompts/
├── skills/
├── hooks/
└── .mcp.json
```
