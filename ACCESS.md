# 访问控制：Private + Read

本仓库是 **GitHub 私有仓库**。未获邀请的人看不到任何内容。获邀且权限为 **Read** 的人可以浏览网页、clone、下载 ZIP，但不能 push、不能改设置、不能邀请其他人。

GitHub **没有**「网页能看、但不能下载」的开关。能看源文件，就能 clone。本仓库因此只放方案介绍和联系方式，不放 QuantLab 源码、数据、Token 和回测产物。

## 给协作者看什么

| 动作 | Read 协作者 | 仓库所有者 |
|---|---|---|
| 打开 GitHub 网页阅读 | 可以 | 可以 |
| `git clone` / Download ZIP | 可以 | 可以 |
| 提 Issue / PR（若未关闭） | 视仓库设置 | 可以 |
| `git push`、改 Settings | 不可以 | 可以 |
| 邀请其他人 | 不可以 | 可以 |

## 邀请只读协作者

先向对方要 **GitHub 用户名**。没有账号需先注册。

### 方式 A：命令行（个人仓库请用这个）

个人账户网页邀请时，界面常常默认给 **Write**。要用 Read，在本机执行：

```bash
gh api -X PUT repos/zwm521gmailcom/quantlab-intro/collaborators/对方用户名 -f permission=pull
```

`permission=pull` 对应 Read。对方会收到邀请邮件，接受后即可打开本仓库。

核对权限：

```bash
gh api repos/zwm521gmailcom/quantlab-intro/collaborators/对方用户名/permission --jq '{user: .user.login, permission: .permission, role: .role_name}'
```

期望结果：`permission` 为 `read`。

### 方式 B：网页

1. 打开 https://github.com/zwm521gmailcom/quantlab-intro
2. **Settings → Collaborators → Add people**
3. 搜索对方 GitHub 用户名
4. 若出现角色选项，选 **Read**，不要选 Write / Admin
5. 发送邀请，等对方接受

如果网页没有角色选项，改用方式 A。

### 方式 C：组织仓库（多人长期协作更稳）

把仓库转到 GitHub Organization 后，网页即可正式选择 Read / Triage / Write / Maintain / Admin，并可按团队授权。需要固定只读分享时，这是最清楚的做法。

## 撤权

```bash
gh api -X DELETE repos/zwm521gmailcom/quantlab-intro/collaborators/对方用户名
```

或在 **Settings → Collaborators** 里 Remove。撤权后对方立刻打不开 GitHub 网页；本地已经 clone 走的副本无法远程收回。

## 不要做的事

- 不要把本仓库改成 Public
- 不要给只想阅读的人 Write / Admin
- 不要在本仓库提交源码、`.env`、Tushare Token、行情 Parquet、回测结果
- 不要用 git 同步 `quantlab_runtime/`
