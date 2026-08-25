# 量潮招聘工作教程

本教程面向生产实习课程的学员，介绍量潮招聘的工作流程和工具使用。

## 概述

量潮招聘是量潮科技的招聘管理系统，用于管理从候选人投递到入职的全流程。系统使用 `qtrecurit` CLI 工具进行邮件发送和流程管理。

## 招聘流程

量潮招聘遵循以下标准流程：

```
候选人投递 → 准入问卷 → 简历筛选 → 笔试 → 面试 → 录用/实训邀请
```

### 1. 候选人投递

候选人通过邮件投递简历和求职信到 `hr@quanttide.com`。邮件主题格式为「姓名-学校-应聘岗位」。

### 2. 准入问卷

收到投递后，首先发送准入问卷邮件：

```bash
qtrecurit access survey --to candidate@example.com --name 张三
```

问卷链接会自动从缓存获取，无需手动输入。

### 3. 简历筛选

候选人提交问卷后，HR 会审核简历和问卷内容，决定是否进入下一环节。

### 4. 笔试

通过筛选的候选人会收到笔试邀请：

```bash
qtrecurit access exam --to candidate@example.com --name 张三
```

### 5. 面试

笔试通过后，安排面试：

```bash
qtrecurit access interview --to candidate@example.com --name 张三 --position 数据工程师 --time "6月20日 10:00"
```

### 6. 录用/实训邀请

面试通过后，根据岗位情况发送录用通知或实训邀请：

```bash
qtrecurit access invite --to candidate@example.com --name 张三
```

## 常用命令

### 查看候选人投递

```bash
lark-cli mail +triage --mailbox hr@quanttide.com --max 20
```

### 查看已发送邮件

```bash
# 查看已发送问卷
FOLDER_ID=$(qtrecurit cache show-folder-id --name "已发送问卷")
lark-cli mail +triage --mailbox hr@quanttide.com --filter "{\"folder\":\"$FOLDER_ID\"}" --max 10

# 查看已发送笔试
FOLDER_ID=$(qtrecurit cache show-folder-id --name "已发送笔试")
lark-cli mail +triage --mailbox hr@quanttide.com --filter "{\"folder\":\"$FOLDER_ID\"}" --max 10
```

### 缓存管理

```bash
# 查看问卷链接
qtrecurit cache show-survey

# 查看二维码
qtrecurit cache show-qr

# 查看文件夹 ID
qtrecurit cache show-folder-id --name "已发送问卷"
```

## 注意事项

1. **邮件发送间隔**：批量发送邮件时，每封间隔 1-2 秒，避免并发冲突
2. **自动归档**：发送邮件后，系统会自动将投递邮件归档到对应文件夹
3. **模板变量**：邮件模板支持 `{{name}}` 等变量，会自动替换为候选人姓名

## 常见问题

### Q: 如何查看候选人是否已填写问卷？
A: 查看「已发送问卷」文件夹，或搜索候选人邮箱的回复邮件。

### Q: 候选人邮箱缺失怎么办？
A: 联系相关负责人补充邮箱，或跳过该候选人后续处理。

### Q: 二维码过期了怎么办？
A: 在飞书群设置中生成新的二维码，然后更新缓存：
```bash
qtrecurit cache set-qr /path/to/new_qr.png
```

## 相关文档

- [发送准入问卷邮件](../../apps/qtrecurit/docs/user-guide/send-survey-email.md)
- [发送实训邀请邮件](../../apps/qtrecurit/docs/user-guide/send-invite-email.md)
- [发送考核邀请邮件](../../apps/qtrecurit/docs/user-guide/send-exam-email.md)
