# 贡献规范

本规范用于个人项目的日常开发，目标是保持流程简单，同时让需求、代码修改和提交记录能够相互追踪。

## 开发流程

除极小的文案修正或无风险调整外，建议按照下面的流程进行开发：

1. 先创建 Issue，说明要解决的问题、需求或重构目标。
2. 从 `main` 创建对应的开发分支。
3. 在分支中完成开发并提交代码。
4. 创建 Pull Request，目标分支为 `main`。
5. 在 PR 中关联对应 Issue，例如：`Closes #12`。
6. 确认 CI、测试和自查通过后再合并。
7. PR 合并后，由 GitHub 自动关闭已关联的 Issue。

推荐的最小闭环：

`Issue → Branch → Commit → Pull Request → CI → Merge → Close Issue`

## 分支命名

推荐使用以下格式：

- `feat/<issue-number>-<short-name>`：新功能
- `fix/<issue-number>-<short-name>`：Bug 修复
- `refactor/<issue-number>-<short-name>`：重构
- `docs/<issue-number>-<short-name>`：文档
- `test/<issue-number>-<short-name>`：测试
- `chore/<issue-number>-<short-name>`：构建、工具链或维护任务

示例：

- `feat/12-recurring-reminder`
- `fix/18-missed-notification`
- `refactor/21-scheduler`

## Commit 规范

推荐使用 Conventional Commits 风格：

- `feat: 添加周期提醒`
- `fix: 修复系统休眠后提醒丢失`
- `refactor: 拆分调度器模块`
- `docs: 更新架构说明`
- `test: 添加调度器测试`
- `chore: 更新开发工具配置`

一次 Commit 尽量只表达一个明确的修改意图。

如果希望加强可追踪性，可以在 Commit 中附带 Issue 编号：

`feat: 添加周期提醒 (#12)`

## Issue 规范

创建 Issue 时，应尽量说明：

- 为什么需要做这件事
- 当前存在什么问题
- 希望达到什么目标
- 有哪些明确的验收标准

功能和 Bug 尽量使用仓库提供的 Issue 模板。

## Pull Request 规范

一个 PR 应尽量只解决一个明确的问题。

PR 中建议包含：

- 本次修改做了什么
- 为什么需要修改
- 关联的 Issue
- 如何验证修改正确
- 是否存在兼容性、性能或其他影响

如果 PR 完成后应关闭对应 Issue，推荐使用：

`Closes #12`

## 合并要求

合并前至少确认：

- 修改内容已经自查
- 相关测试通过
- CI 检查通过
- 没有明显遗留调试代码
- 文档在必要时已经同步更新

个人项目不强制要求额外 Reviewer，但仍建议通过 PR 完成合并，以保留完整的变更上下文。

## 例外情况

以下类型的修改可以视情况直接提交到 `main`：

- 拼写错误
- 极小的 README 修正
- 不影响行为的简单文案调整

功能开发、Bug 修复、重构和架构变更原则上应遵循 Issue 驱动流程。
