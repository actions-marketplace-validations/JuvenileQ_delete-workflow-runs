### 获取项目中所有工作流

**请求接口：**
```http
https://api.github.com/repos/:owner/:repo/actions/workflows?auth=xxxxx
```
**请求类型：**`GET`

**请求参数：**

| 参数名     | 类型       | 必选 | 说明      |
|---------|----------|----|:--------|
| `auth`  | `string` | 是  | 用户token |
| `owner` | `string` | 是  | 用户名     |
| `repo`  | `string` | 是  | 仓库名     |

**返回结果：**
```json
{
  "total_count": 2,
  "workflows": [
    {
      "id": 57669440,
      "node_id": "W_kwDOJk3fR84Db_dA",
      "name": "juejin",
      "path": ".github/workflows/juejin.yml",
      "state": "active",
      "created_at": "2023-05-19T02:45:34.000Z",
      "updated_at": "2023-05-27T16:41:26.000Z",
      "url": "https://api.github.com/repos/JuvenileQ/juejin/actions/workflows/57669440",
      "html_url": "https://github.com/JuvenileQ/juejin/blob/master/.github/workflows/juejin.yml",
      "badge_url": "https://github.com/JuvenileQ/juejin/workflows/juejin/badge.svg"
    },
    {
      "id": 57669441,
      "node_id": "W_kwDOJk3fR84Db_dB",
      "name": "sspanel",
      "path": ".github/workflows/sspanel.yml",
      "state": "disabled_fork",
      "created_at": "2023-05-19T02:45:34.000Z",
      "updated_at": "2023-05-19T02:45:34.000Z",
      "url": "https://api.github.com/repos/JuvenileQ/juejin/actions/workflows/57669441",
      "html_url": "https://github.com/JuvenileQ/juejin/blob/master/.github/workflows/sspanel.yml",
      "badge_url": "https://github.com/JuvenileQ/juejin/workflows/sspanel/badge.svg"
    }
  ]
}
```

### 列出指定workflow的所有 workflow_runs 详细信息
**请求接口：**
```http
https://api.github.com/repos/:owner/:repo/actions/workflows/:workflow_id/runs?auth=xxxxx
```
**请求类型：**`GET`

**请求参数：**

| 参数名           | 类型       | 必选 | 说明          |
|---------------|----------|----|:------------|
| `auth`        | `string` | 是  | 用户token     |
| `owner`       | `string` | 是  | 用户名         |
| `repo`        | `string` | 是  | 仓库名         |
| `workflow_id` | `string` | 是  | workflow id |

**返回结果：**
```json
{
  "total_count": 6,
  "workflow_runs": [
    {
      "id": 5138304534,
      "name": "juejin",
      "node_id": "WFR_kwLOJk3fR88AAAABMkROFg",
      "head_branch": "master",
      "head_sha": "7eda106e06d1f3276aece3536ac83295ac7fcb8d",
      "path": ".github/workflows/juejin.yml",
      "display_title": "juejin",
      "run_number": 24,
      "event": "schedule",
      "status": "completed",
      "conclusion": "success",
      "workflow_id": 57669440,
      "check_suite_id": 13285280967,
      "check_suite_node_id": "CS_kwDOJk3fR88AAAADF91Mxw",
      "url": "https://api.github.com/repos/JuvenileQ/juejin/actions/runs/5138304534",
      "html_url": "https://github.com/JuvenileQ/juejin/actions/runs/5138304534",
      "pull_requests": [],
      "created_at": "2023-05-31T22:31:36Z",
      "updated_at": "2023-05-31T22:32:25Z",
      "actor": {
        "login": "JuvenileQ",
        "id": 39209399,
        "node_id": "xxxxxx"
      },
      "run_attempt": 1,
      "referenced_workflows": [],
      "run_started_at": "2023-05-31T22:31:36Z",
      "triggering_actor": {
        "login": "JuvenileQ",
        "id": 39209399,
        "node_id": "MDQ6VXNlcjM5MjA5Mzk5",
        "avatar_url": "https://avatars.githubusercontent.com/u/39209399?v=4",
        "gravatar_id": "",
        "url": "https://api.github.com/users/JuvenileQ",
        "html_url": "https://github.com/JuvenileQ",
        "followers_url": "https://api.github.com/users/JuvenileQ/followers",
        "following_url": "https://api.github.com/users/JuvenileQ/following{/other_user}",
        "gists_url": "https://api.github.com/users/JuvenileQ/gists{/gist_id}",
        "starred_url": "https://api.github.com/users/JuvenileQ/starred{/owner}{/repo}",
        "subscriptions_url": "https://api.github.com/users/JuvenileQ/subscriptions",
        "organizations_url": "https://api.github.com/users/JuvenileQ/orgs",
        "repos_url": "https://api.github.com/users/JuvenileQ/repos",
        "events_url": "https://api.github.com/users/JuvenileQ/events{/privacy}",
        "received_events_url": "https://api.github.com/users/JuvenileQ/received_events",
        "type": "User",
        "site_admin": false
      },
      "repository": {
        "id": 642637639,
        "node_id": "R_kgDOJk3fRw",
        "name": "juejin",
        "full_name": "JuvenileQ/juejin",
        "private": false,
        "owner": {
          "login": "JuvenileQ",
          "id": 39209399,
          "node_id": "MDQ6VXNlcjM5MjA5Mzk5",
          "avatar_url": "https://avatars.githubusercontent.com/u/39209399?v=4",
          "gravatar_id": "",
          "url": "https://api.github.com/users/JuvenileQ",
          "html_url": "https://github.com/JuvenileQ",
          "followers_url": "https://api.github.com/users/JuvenileQ/followers",
          "following_url": "https://api.github.com/users/JuvenileQ/following{/other_user}",
          "gists_url": "https://api.github.com/users/JuvenileQ/gists{/gist_id}",
          "starred_url": "https://api.github.com/users/JuvenileQ/starred{/owner}{/repo}",
          "subscriptions_url": "https://api.github.com/users/JuvenileQ/subscriptions",
          "organizations_url": "https://api.github.com/users/JuvenileQ/orgs",
          "repos_url": "https://api.github.com/users/JuvenileQ/repos",
          "events_url": "https://api.github.com/users/JuvenileQ/events{/privacy}",
          "received_events_url": "https://api.github.com/users/JuvenileQ/received_events",
          "type": "User",
          "site_admin": false
        },
        "html_url": "https://github.com/JuvenileQ/juejin",
        "description": "基于 GitHub Actions 签到 SSPANEL 面板、掘金社区，支持多账号多网站。",
        "fork": true,
        "url": "https://api.github.com/repos/JuvenileQ/juejin",
        "forks_url": "https://api.github.com/repos/JuvenileQ/juejin/forks",
        "keys_url": "https://api.github.com/repos/JuvenileQ/juejin/keys{/key_id}",
        "collaborators_url": "https://api.github.com/repos/JuvenileQ/juejin/collaborators{/collaborator}",
        "teams_url": "https://api.github.com/repos/JuvenileQ/juejin/teams",
        "hooks_url": "https://api.github.com/repos/JuvenileQ/juejin/hooks",
        "issue_events_url": "https://api.github.com/repos/JuvenileQ/juejin/issues/events{/number}",
        "events_url": "https://api.github.com/repos/JuvenileQ/juejin/events",
        "assignees_url": "https://api.github.com/repos/JuvenileQ/juejin/assignees{/user}",
        "branches_url": "https://api.github.com/repos/JuvenileQ/juejin/branches{/branch}",
        "tags_url": "https://api.github.com/repos/JuvenileQ/juejin/tags",
        "blobs_url": "https://api.github.com/repos/JuvenileQ/juejin/git/blobs{/sha}",
        "git_tags_url": "https://api.github.com/repos/JuvenileQ/juejin/git/tags{/sha}",
        "git_refs_url": "https://api.github.com/repos/JuvenileQ/juejin/git/refs{/sha}",
        "trees_url": "https://api.github.com/repos/JuvenileQ/juejin/git/trees{/sha}",
        "statuses_url": "https://api.github.com/repos/JuvenileQ/juejin/statuses/{sha}",
        "languages_url": "https://api.github.com/repos/JuvenileQ/juejin/languages",
        "stargazers_url": "https://api.github.com/repos/JuvenileQ/juejin/stargazers",
        "contributors_url": "https://api.github.com/repos/JuvenileQ/juejin/contributors",
        "subscribers_url": "https://api.github.com/repos/JuvenileQ/juejin/subscribers",
        "subscription_url": "https://api.github.com/repos/JuvenileQ/juejin/subscription",
        "commits_url": "https://api.github.com/repos/JuvenileQ/juejin/commits{/sha}",
        "git_commits_url": "https://api.github.com/repos/JuvenileQ/juejin/git/commits{/sha}",
        "comments_url": "https://api.github.com/repos/JuvenileQ/juejin/comments{/number}",
        "issue_comment_url": "https://api.github.com/repos/JuvenileQ/juejin/issues/comments{/number}",
        "contents_url": "https://api.github.com/repos/JuvenileQ/juejin/contents/{+path}",
        "compare_url": "https://api.github.com/repos/JuvenileQ/juejin/compare/{base}...{head}",
        "merges_url": "https://api.github.com/repos/JuvenileQ/juejin/merges",
        "archive_url": "https://api.github.com/repos/JuvenileQ/juejin/{archive_format}{/ref}",
        "downloads_url": "https://api.github.com/repos/JuvenileQ/juejin/downloads",
        "issues_url": "https://api.github.com/repos/JuvenileQ/juejin/issues{/number}",
        "pulls_url": "https://api.github.com/repos/JuvenileQ/juejin/pulls{/number}",
        "milestones_url": "https://api.github.com/repos/JuvenileQ/juejin/milestones{/number}",
        "notifications_url": "https://api.github.com/repos/JuvenileQ/juejin/notifications{?since,all,participating}",
        "labels_url": "https://api.github.com/repos/JuvenileQ/juejin/labels{/name}",
        "releases_url": "https://api.github.com/repos/JuvenileQ/juejin/releases{/id}",
        "deployments_url": "https://api.github.com/repos/JuvenileQ/juejin/deployments"
      },
      "head_repository": {
        "id": 642637639,
        "node_id": "R_kgDOJk3fRw",
        "name": "juejin",
        "full_name": "JuvenileQ/juejin",
        "private": false,
        "owner": {
          "login": "JuvenileQ",
          "id": 39209399,
          "node_id": "MDQ6VXNlcjM5MjA5Mzk5",
          "avatar_url": "https://avatars.githubusercontent.com/u/39209399?v=4",
          "gravatar_id": "",
          "url": "https://api.github.com/users/JuvenileQ",
          "html_url": "https://github.com/JuvenileQ",
          "followers_url": "https://api.github.com/users/JuvenileQ/followers",
          "following_url": "https://api.github.com/users/JuvenileQ/following{/other_user}",
          "gists_url": "https://api.github.com/users/JuvenileQ/gists{/gist_id}",
          "starred_url": "https://api.github.com/users/JuvenileQ/starred{/owner}{/repo}",
          "subscriptions_url": "https://api.github.com/users/JuvenileQ/subscriptions",
          "organizations_url": "https://api.github.com/users/JuvenileQ/orgs",
          "repos_url": "https://api.github.com/users/JuvenileQ/repos",
          "events_url": "https://api.github.com/users/JuvenileQ/events{/privacy}",
          "received_events_url": "https://api.github.com/users/JuvenileQ/received_events",
          "type": "User",
          "site_admin": false
        },
        "html_url": "https://github.com/JuvenileQ/juejin",
        "description": "基于 GitHub Actions 签到 SSPANEL 面板、掘金社区，支持多账号多网站。",
        "fork": true,
        "url": "https://api.github.com/repos/JuvenileQ/juejin",
        "forks_url": "https://api.github.com/repos/JuvenileQ/juejin/forks",
        "keys_url": "https://api.github.com/repos/JuvenileQ/juejin/keys{/key_id}",
        "collaborators_url": "https://api.github.com/repos/JuvenileQ/juejin/collaborators{/collaborator}",
        "teams_url": "https://api.github.com/repos/JuvenileQ/juejin/teams",
        "hooks_url": "https://api.github.com/repos/JuvenileQ/juejin/hooks",
        "issue_events_url": "https://api.github.com/repos/JuvenileQ/juejin/issues/events{/number}",
        "events_url": "https://api.github.com/repos/JuvenileQ/juejin/events",
        "assignees_url": "https://api.github.com/repos/JuvenileQ/juejin/assignees{/user}",
        "branches_url": "https://api.github.com/repos/JuvenileQ/juejin/branches{/branch}",
        "tags_url": "https://api.github.com/repos/JuvenileQ/juejin/tags",
        "blobs_url": "https://api.github.com/repos/JuvenileQ/juejin/git/blobs{/sha}",
        "git_tags_url": "https://api.github.com/repos/JuvenileQ/juejin/git/tags{/sha}",
        "git_refs_url": "https://api.github.com/repos/JuvenileQ/juejin/git/refs{/sha}",
        "trees_url": "https://api.github.com/repos/JuvenileQ/juejin/git/trees{/sha}",
        "statuses_url": "https://api.github.com/repos/JuvenileQ/juejin/statuses/{sha}",
        "languages_url": "https://api.github.com/repos/JuvenileQ/juejin/languages",
        "stargazers_url": "https://api.github.com/repos/JuvenileQ/juejin/stargazers",
        "contributors_url": "https://api.github.com/repos/JuvenileQ/juejin/contributors",
        "subscribers_url": "https://api.github.com/repos/JuvenileQ/juejin/subscribers",
        "subscription_url": "https://api.github.com/repos/JuvenileQ/juejin/subscription",
        "commits_url": "https://api.github.com/repos/JuvenileQ/juejin/commits{/sha}",
        "git_commits_url": "https://api.github.com/repos/JuvenileQ/juejin/git/commits{/sha}",
        "comments_url": "https://api.github.com/repos/JuvenileQ/juejin/comments{/number}",
        "issue_comment_url": "https://api.github.com/repos/JuvenileQ/juejin/issues/comments{/number}",
        "contents_url": "https://api.github.com/repos/JuvenileQ/juejin/contents/{+path}",
        "compare_url": "https://api.github.com/repos/JuvenileQ/juejin/compare/{base}...{head}",
        "merges_url": "https://api.github.com/repos/JuvenileQ/juejin/merges",
        "archive_url": "https://api.github.com/repos/JuvenileQ/juejin/{archive_format}{/ref}",
        "downloads_url": "https://api.github.com/repos/JuvenileQ/juejin/downloads",
        "issues_url": "https://api.github.com/repos/JuvenileQ/juejin/issues{/number}",
        "pulls_url": "https://api.github.com/repos/JuvenileQ/juejin/pulls{/number}",
        "milestones_url": "https://api.github.com/repos/JuvenileQ/juejin/milestones{/number}",
        "notifications_url": "https://api.github.com/repos/JuvenileQ/juejin/notifications{?since,all,participating}",
        "labels_url": "https://api.github.com/repos/JuvenileQ/juejin/labels{/name}",
        "releases_url": "https://api.github.com/repos/JuvenileQ/juejin/releases{/id}",
        "deployments_url": "https://api.github.com/repos/JuvenileQ/juejin/deployments"
      }
    },
    {
      "id": 5129763754,
      "name": "juejin",
      "node_id": "WFR_kwLOJk3fR88AAAABMcH7qg",
      "head_branch": "master",
      "path": ".github/workflows/juejin.yml",
      "display_title": "juejin",
      "run_number": 20,
      "event": "workflow_dispatch",
      "status": "completed",
      "conclusion": "failure",
      "workflow_id": 57669440,
      "check_suite_id": 13262180470,
      "check_suite_node_id": "CS_kwDOJk3fR88AAAADFnzQdg",
      "url": "https://api.github.com/repos/JuvenileQ/juejin/actions/runs/5129763754",
      "html_url": "https://github.com/JuvenileQ/juejin/actions/runs/5129763754",
      "pull_requests": [],
      "created_at": "2023-05-31T06:50:29Z",
      "updated_at": "2023-05-31T06:51:01Z",
      "run_attempt": 1,
      "run_started_at": "2023-05-31T06:50:29Z",
      "previous_attempt_url": null,
      "workflow_url": "https://api.github.com/repos/JuvenileQ/juejin/actions/workflows/57669440",
    }
  ]
}
```