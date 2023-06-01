<h1 align="center">Delete-Workflow-Runs</h1>

<p align="center"><a href="README_CN.md">简体中文</a> &nbsp &nbsp <a href="README.md">English</a></p>

本项目用于删除仓库中 GitHub Actions 所生成的 Workflow Runs。此操作（用 JavaScript 编写）包装两个工作流运行 API：

* [**List repository workflows**](https://docs.github.com/en/free-pro-team@latest/rest/reference/actions#list-repository-workflows) -- 列出仓库中的Workflows。

* [**List workflow runs**](https://docs.github.com/en/free-pro-team@latest/rest/reference/actions#list-workflow-runs) -- 列出 Workflows 的所有 Workflow Runs。

* [**Delete a workflow run**](https://docs.github.com/en/free-pro-team@latest/rest/reference/actions#delete-a-workflow-run) -- 删除指定的 Workflow Runs。

该操作将计算到目前为止每个工作流运行的保留天数，然后使用此数字与您为输入参数 "[**`retain_days`**](#3-retain_days)" 指定的天数进行比较。如果工作流运行的保留天数已达到（等于或大于）指定数字，则将删除工作流运行。

## Inputs
### 1. `token`
#### 必须: YES
#### 默认: `${{ github.token }}`
用于进行身份验证的令牌。
* 如果 **workflow runs** 是在当前仓库的 **Actions** 中运行，则可以使用 **`github.token`**。更多详细信息，请参见 [**`GITHUB_TOKEN`**](https://docs.github.com/en/free-pro-team@latest/actions/reference/authentication-in-a-workflow)。
* 如果 **workflow runs** 在另一个存储库中，则需要使用权限范围为 **`repo`** 的个人访问令牌 （PAT）。有关详细信息，请参阅"[Creating a personal access token](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token)"。


### 2. `repository`
#### 必须: YES
#### 默认: `${{ github.repository }}`
**workflow runs**所在的仓库名称。

### 3. `retain_days`
#### 必须: YES
#### 默认: 30
用于与每个 **workflow** 的保留天数进行比较的天数。

### 4. `keep_minimum_runs`
#### 必须: YES
#### 默认: 6
每个 **workflow** 要保留的 **workflow runs** 数量。

### 5. `delete_workflow_pattern`
#### 必须: NO
#### 默认: 'all'
**workflow** 的名称或文件名。如果未设置，则它将面向所有 **workflow**。

### 6. `delete_workflow_by_state_pattern`
#### 必须: NO
#### 默认: 'all'
按状态删除工作流：active, deleted, disabled_fork, disabled_inactivity, disabled_manually

### 7. `delete_run_by_conclusion_pattern`
#### 必须: NO
#### 默认: 'all'
按结论删除工作流：action_required, cancelled, failure, skipped, success

### 8. `dry_run`
#### 必须: NO
仅记录操作，不执行任何删除操作。


## 示例
### 在定时任务中执行, 详见 [schedule event](https://docs.github.com/en/free-pro-team@latest/actions/reference/events-that-trigger-workflows#schedule).
> **Tip:** 建议使用定时任务执行工作流，该方法可以定期自动删除旧的工作流运行。

```yaml
name: Delete old workflow runs
on:
  schedule:
    - cron: '0 0 1 * *'
# Run monthly, at 00:00 on the 1st day of month.

jobs:
  del_runs:
    runs-on: ubuntu-latest
    steps:
      - name: 删除 workflow runs
        uses: JuvenileQ/delete-workflow-runs@main
        with:
          token: ${{ github.token }}
          repository: ${{ github.repository }}
          retain_days: 30
          keep_minimum_runs: 6
```

### 手动执行工作流，详见 [workflow_dispatch event](https://docs.github.com/en/free-pro-team@latest/actions/reference/events-that-trigger-workflows#workflow_dispatch).

```yaml
name: Delete old workflow runs
on:
  workflow_dispatch:
    inputs:
      days:
        description: 'Number of days.'
        required: true
        default: 30
      minimum_runs:
        description: 'The minimum runs to keep for each workflow.'
        required: true
        default: 6
      delete_workflow_pattern:
        description: 'The name or filename of the workflow. if not set then it will target all workflows.'
        required: false
      delete_workflow_by_state_pattern:
        description: 'Remove workflow by state: active, deleted, disabled_fork, disabled_inactivity, disabled_manually'
        required: true
        default: "All"
        type: choice
        options:
          - "All"
          - active
          - deleted
          - disabled_inactivity
          - disabled_manually
      delete_run_by_conclusion_pattern:
        description: 'Remove workflow by conclusion: action_required, cancelled, failure, skipped, success'
        required: true
        default: "All"
        type: choice
        options:
          - "All"
          - action_required
          - cancelled
          - failure
          - skipped
          - success
      dry_run:
        description: 'Only log actions, do not perform any delete operations.'
        required: false

jobs:
  del_runs:
    runs-on: ubuntu-latest
    steps:
      - name: Delete workflow runs
        uses: JuvenileQ/delete-workflow-runs@main
        with:
          token: ${{ github.token }}
          repository: ${{ github.repository }}
          retain_days: ${{ github.event.inputs.days }}
          keep_minimum_runs: ${{ github.event.inputs.minimum_runs }}
          delete_workflow_pattern: ${{ github.event.inputs.delete_workflow_pattern }}
          delete_workflow_by_state_pattern: ${{ github.event.inputs.delete_workflow_by_state_pattern }}
          delete_run_by_conclusion_pattern: ${{ github.event.inputs.delete_run_by_conclusion_pattern }}
          dry_run: ${{ github.event.inputs.dry_run }}
```

## License
The scripts and documentation in this project are released under the [MIT License](LICENSE).