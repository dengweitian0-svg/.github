# 贡献规范

本规范用于个人项目的日常开发，目标是保持流程简单，同时让需求、代码修改和提交记录能够相互追踪。

## 分支策略

项目采用 `main + dev` 双主干模式：

- `main`：稳定分支，不作为日常开发分支。仅用于经过验证的版本更新和正式发布。
- `dev`：日常开发集成分支。功能开发、Bug 修复、重构等工作应基于 `dev` 开始，并最终合并回 `dev`。

原则上不要直接在 `main` 上进行功能开发，也不要把普通功能分支直接合并到 `main`。

推荐的分支关系：

`main ← dev ← feat/fix/refactor/docs/test/chore`

日常开发完成后先进入 `dev`；当 `dev` 中积累的修改达到一个可发布版本并完成验证后，再通过 Pull Request 将 `dev` 合并到 `main`，完成一次版本级更新。

## 开发流程

除极小的文案修正或无风险调整外，建议按照下面的流程进行开发：

1. 先创建 Issue，说明要解决的问题、需求或重构目标。
2. 从最新的 `dev` 创建对应的开发分支。
3. 在开发分支中完成修改并提交代码。
4. 创建 Pull Request，目标分支为 `dev`。
5. 在 PR 中关联对应 Issue，例如：`Closes #12`。
6. 确认 CI、测试和自查通过后，将 PR 合并到 `dev`。
7. PR 合并后，由 GitHub 自动关闭已关联的 Issue。
8. 当准备发布新版本时，再创建 `dev → main` 的版本发布 PR。
9. 版本发布 PR 验证通过后合并到 `main`，完成版本更新。

日常开发最小闭环：

`Issue → Branch(from dev) → Commit → Pull Request(to dev) → CI → Merge dev → Close Issue`

版本发布流程：

`dev → Release PR → CI / 验证 → main → Version Release`

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

开发分支应从 `dev` 创建，例如：

```bash
git switch dev
git pull
git switch -c feat/12-recurring-reminder
```

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

### 日常开发 PR

功能、Bug、重构、文档、测试等日常开发 PR：

- 来源：`feat/*`、`fix/*`、`refactor/*` 等开发分支
- 目标：`dev`
- 原则上一个 PR 只解决一个明确问题
- 应关联对应 Issue

### 版本发布 PR

准备发布一个新版本时：

- 来源：`dev`
- 目标：`main`
- 用于将已经在 `dev` 中集成并验证的修改发布到稳定分支
- 不应在该 PR 中临时加入未经 `dev` 验证的新功能

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

## main 分支规则

`main` 代表当前稳定、可发布的版本，应保持相对稳定。

原则上：

- 不直接在 `main` 上进行日常功能开发。
- 普通功能分支不直接合并到 `main`。
- 日常修改首先进入 `dev`。
- 只有准备完成一个版本更新时，才将 `dev` 合并到 `main`。

## 例外情况

极小的文案、仓库元数据或紧急维护修改可以视情况简化流程，但如果修改会影响程序行为，原则上仍应先进入 `dev`，再随版本发布进入 `main`。
