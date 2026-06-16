# Issue tracker: GitHub

该仓库的 issue 和 PRD 使用 GitHub Issues 管理。所有操作通过 `gh` CLI 执行。

## 使用约定

- **创建 issue**：`gh issue create --title "..." --body "..."`。长文本 body 使用 heredoc。
- **读取 issue**：`gh issue view <number> --comments`，配合 `jq` 过滤评论和标签。
- **列出 issue**：`gh issue list --state open --json number,title,body,labels,comments --jq '"'"'[.[] | {number, title, body, labels: [.labels[].name], comments: [.comments[].body]}]'"'"'`，配合 `--label` 和 `--state` 过滤。
- **评论 issue**：`gh issue comment <number> --body "..."`
- **添加/移除标签**：`gh issue edit <number> --add-label "..."` / `--remove-label "..."`
- **关闭 issue**：`gh issue close <number> --comment "..."`

仓库信息从 `git remote -v` 自动推断——`gh` 在克隆目录内运行时会自动使用当前仓库。

## 当技能说"发布到议题追踪器"

创建一个 GitHub issue。

## 当技能说"获取相关工单"

运行 `gh issue view <number> --comments`。
