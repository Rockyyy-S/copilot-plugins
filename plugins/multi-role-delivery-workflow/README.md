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

## 4. 角色列表

- `project-coordinator`：项目总协调
- `product-planner`：产品规划官
- `architecture-designer`：架构设计师
- `frontend-expert`：前端专家
- `backend-expert`：后端专家
- `mobile-expert`：移动端开发专家
- `mini-program-expert`：微信小程序开发专家
- `ux-ui-designer`：UX/UI设计师
- `brand-designer`：品牌设计师
- `qa-specialist`：QA专家
- `security-reviewer`：安全审查师
- `devops-engineer`：运维工程师
- `release-manager`：发布经理
- `technical-writer`：文档撰写员
- `data-analyst`：数据分析师
- `dx-champion`：DX工程效率官
- `business-development-manager`：新业务拓展经理

## 5. 升级与兼容

- 升级前先看 `CHANGELOG.md`，确认是否存在破坏性变更。
- 对于 `hooks/` 规则变更，建议先在测试仓验证。
- 对于 `agents/` handoff 变更，建议回归 0to1 主流程一次。

## 6. 目录结构

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
