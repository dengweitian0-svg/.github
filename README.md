# GitHub 默认开发规范

这个仓库用于维护个人 GitHub 项目的默认社区健康文件（Community Health Files）。

当其他仓库没有定义自己的对应文件时，可以默认使用这里的 Issue 模板、Pull Request 模板和贡献规范。

当前包含：

- Bug Issue 模板
- 功能需求 Issue 模板
- 重构 Issue 模板
- Pull Request 模板
- `CONTRIBUTING.md` 贡献规范

## 分支策略

默认采用 `main + dev` 双主干模式：

- `main`：稳定分支，不用于日常开发，仅用于版本级更新和正式发布。
- `dev`：日常开发集成分支，所有功能、Bug 修复、重构等修改应优先合并到这里。

日常开发关系：

`main ← dev ← feat/fix/refactor/docs/test/chore`

日常开发流程：

`Issue → 从 dev 创建分支 → Commit → Pull Request 到 dev → CI → Merge dev → Close Issue`

版本发布流程：

`dev → Release PR → CI / 验证 → main → Version Release`

具体规则请查看 `CONTRIBUTING.md`。
