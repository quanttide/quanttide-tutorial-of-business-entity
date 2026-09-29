# ROADMAP

## 内容迁出：公司教程 → 领域教程（已完成）

公司教程是**主体层**（`assets/quanttide-tutorial/default/company`），只讲"量潮科技这家公司怎么做"。领域知识——换个公司也成立的方法——已全部迁往对应领域教程仓库 `quanttide-tutorial-of-*`。

判断规则：**把文档里的"量潮"换成另一家公司，内容还成立吗？**成立 → 迁去领域教程；不成立 → 留在公司教程。

### 迁出结果

29 篇中 28 篇迁入 12 个领域教程仓库，1 篇占位删除。

| # | 目标教程仓库 | 篇数 | 落位 |
|--:|:--|--:|:--|
| 1 | [`quanttide-tutorial-of-agent-engineering`](https://github.com/quanttide/quanttide-tutorial-of-agent-engineering) | 1 | `skill.md` |
| 2 | [`quanttide-tutorial-of-asset-management`](https://github.com/quanttide/quanttide-tutorial-of-asset-management) | 1 | `governance/batch-maintain.md` |
| 3 | [`quanttide-tutorial-of-business-development`](https://github.com/quanttide/quanttide-tutorial-of-business-development) | 1 | `index.md` |
| 4 | [`quanttide-tutorial-of-communication-management`](https://github.com/quanttide/quanttide-tutorial-of-communication-management) | 4 | `index.md`、`channels.md`、`principles.md`、`external-bypass.md` |
| 5 | [`quanttide-tutorial-of-deliberation-management`](https://github.com/quanttide/quanttide-tutorial-of-deliberation-management) | 2 | `how-to-run-effective-meeting.md`、`reduce-founder-dependency-through-meetings.md` |
| 6 | [`quanttide-tutorial-of-devops`](https://github.com/quanttide/quanttide-tutorial-of-devops) | 2 | `stage/release/practice.md`、`stage/test.md` |
| 7 | [`quanttide-tutorial-of-finance-management`](https://github.com/quanttide/quanttide-tutorial-of-finance-management) | 1 | `index.md` |
| 8 | [`quanttide-tutorial-of-narrative-engineering`](https://github.com/quanttide/quanttide-tutorial-of-narrative-engineering) | 3 | `index.md`、`bylaw.md`、`brochure.md` |
| 9 | [`quanttide-tutorial-of-organization-management`](https://github.com/quanttide/quanttide-tutorial-of-organization-management) | 5 | `index.md`、`founder-dependency.md`、`mechanism-design.md`、`culture/index.md`、`culture/how.md` |
| 10 | [`quanttide-tutorial-of-open-source`](https://github.com/quanttide/quanttide-tutorial-of-open-source) | 1 | `license.md` |
| 11 | [`quanttide-tutorial-of-social-media`](https://github.com/quanttide/quanttide-tutorial-of-social-media) | 1 | `wechat.md` |
| 12 | [`quanttide-tutorial-of-strategy-management`](https://github.com/quanttide/quanttide-tutorial-of-strategy-management) | 6 | `business-model.md`、`competence.md`、`challenges.md`、`rule-of-law.md`、`governance-layer.md`、`build-in-public.md` |

删除 1 篇：`connect/README.md`——3 行占位，与 `connect/index.md` 重复，不搬运。

### 新建的两个教程仓库

| 领域 | 仓库 | 承接内容 |
|:--|:--|:--|
| 商务拓展 | `quanttide-tutorial-of-business-development` | 报价 |
| 议事管理 | `quanttide-tutorial-of-deliberation-management` | 开会方法、用会议降低创始人依赖 |

### 留在公司教程（22 篇）

| 文件 | 为什么留 |
|:--|:--|
| `index.md` | 教程入口、三层文档说明、领域教程指引 |
| `intro/index.md` | 新人快速入门 |
| `appendix/definitions.md` | 本公司的定义 |
| `qtdata/`（9 篇） | 量潮数据业务线怎么跑 |
| `qtclass/`（3 篇） | 量潮课堂业务线怎么跑 |
| `qtcloud/`（1 篇） | 量潮云业务线怎么跑 |
| `qtconsult/`（3 篇） | 量潮咨询业务线怎么跑 |
| `qtcrowd/`（1 篇） | 量潮众包业务线怎么跑 |
| `qtrecurit/`（2 篇） | 量潮招聘业务线怎么跑 |

### 收口动作

- [x] 内容写进目标领域教程仓库，按各自仓库的目录组织
- [x] 本仓库删除原文件，`myst.yml` 目录同步
- [x] 本仓库 `index.md` 增「领域教程不在这里」指引段落
- [x] `AGENTS.md` 写入判断规则，防止领域内容再回流
- [x] 迁出后两处教程仓库的指针同步到 `assets/quanttide-tutorial`

### 待办：迁入内容尚未去公司化

迁移是**原样搬运**——内容、案例、口径都保持作者原文，没有改写。其中不少篇目仍带量潮的具体案例（如面试例子、CTO 助理发版、公司财务现状）。按"换成另一家公司还成立吗"这条规则，这些段落应当抽掉或改写成通用表述，但那是内容编辑，需要作者判断，没有在这一轮做。

### 当前公司教程结构

```text
default/company/           # 量潮科技工作教程——只讲"这家公司"
├── index.md
├── intro/                 # 新人入门
├── appendix/              # 定义
├── qtdata/                # 业务线
├── qtclass/
├── qtcloud/
├── qtconsult/
├── qtcrowd/
└── qtrecurit/
```

领域类章节（`agent/`、`asset/`、`business/`、`connect/`、`delib/`、`devops/`、`finance/`、`market/`、`media/`、`org/`、`share/`、`stdn/`、`strategy/`、`write/`）已全部腾空。

## v0.6.0

### 个人视角深度补全

- [ ] 各平台操作指引：飞书、GitHub、企业微信的加入和基础使用步骤
- [ ] 工时申报系统配套培训视频链接（待刘婧怡录制完成）
- [ ] 各岗位差异化指引入口（研发 / 运营 / 商务）

### 文档底座打通

- [ ] 快速入门增加章程和手册的索引链接
- [ ] 说明三层文档的关系：教程在哪、章程在哪、手册在哪

### 新人反馈闭环

- [ ] individual.md 末尾增加"有问题找秘书处"指引
- [ ] FAQ 机制：秘书处收集新人提问，攒够 3-5 条补一篇 FAQ
- [ ] 季度复盘 FAQ 趋势，反推教程优化方向

## 长期

- [ ] 和 HR 团队对齐发布节奏：每次版本发布前同步知识库内容
- [ ] 教程保持框架，各岗位操作细节留在知识库
