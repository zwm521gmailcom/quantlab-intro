# 仓库说明

本仓库是 **公开的方案介绍**，任何人都可以打开链接阅读。里面只有介绍、界面截图和微信二维码，没有 QuantLab 源码、数据、Token 和回测产物。

源码仓库 `quantlab` 保持 **Private**。需要阅读代码时，由所有者另行邀请，默认只给 Read，不要给 Write：

```bash
gh api -X PUT repos/zwm521gmailcom/quantlab/collaborators/对方用户名 -f permission=pull
```

GitHub **没有**「网页能看、但不能下载」的开关。能看文件，就能 clone。所以公开的是介绍，不是源码。

## 不要做的事

- 不要把源码仓库 `quantlab` 改成 Public
- 不要在本仓库提交源码、`.env`、Tushare Token、行情 Parquet、回测结果
- 不要用 git 同步 `quantlab_runtime/`
