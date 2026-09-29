# ROADMAP

## 内容迁出：公司教程 → 领域教程

### 为什么迁

公司教程是**主体层**（`assets/quanttide-tutorial/default/company`），回答的是"量潮科技这家公司怎么做"。领域知识——换个公司也成立的方法——属于领域层，应该在对应领域教程仓库 `quanttide-tutorial-of-*` 里，公司教程只留指针。

迁完之后两侧的边界：

| | 公司教程（本仓库） | 领域教程 `quanttide-tutorial-of-*` |
|:--|:--|:--|
| 回答 | 量潮科技怎么做 | 这门知识是什么、通用方法 |
| 素材 | 公司口径、制度、业务线、案例 | 方法、原则、流程、验收标准 |
| 变化频率 | 随公司调整 | 随领域认知 |
| 读者 | 新人、在职成员 | 任何做这件事的人 |

一条判断规则：**把文档里的"量潮"换成另一家公司，内容还成立吗？**成立 → 迁去领域教程；不成立 → 留在公司教程。

### 迁出清单

共 31 篇，按目标教程分组。

#### 智能体工程 → [`quanttide-tutorial-of-agent-engineering`](https://github.com/quanttide/quanttide-tutorial-of-agent-engineering)

- [ ] `agent/skill.md`

#### 资产管理 → [`quanttide-tutorial-of-asset-management`](https://github.com/quanttide/quanttide-tutorial-of-asset-management)

- [ ] `asset/batch-maintain.md`

#### 商务拓展 → **【待建教程仓库】**

- [ ] `business/quotation.md`

#### 沟通管理 → [`quanttide-tutorial-of-communication-management`](https://github.com/quanttide/quanttide-tutorial-of-communication-management)

- [ ] `connect/README.md`
- [ ] `connect/channels.md`
- [ ] `connect/external-bypass.md`
- [ ] `connect/index.md`
- [ ] `connect/principles.md`

#### 议事管理 → **【待建教程仓库】**

- [ ] `delib/how-to-run-effective-meeting.md`
- [ ] `delib/reduce-founder-dependency-through-meetings.md`

#### DevOps 工程 → [`quanttide-tutorial-of-devops`](https://github.com/quanttide/quanttide-tutorial-of-devops)

- [ ] `devops/release.md`
- [ ] `devops/test.md`

#### 财务管理 → [`quanttide-tutorial-of-finance-management`](https://github.com/quanttide/quanttide-tutorial-of-finance-management)

- [ ] `finance/index.md`

#### 新媒体运营 → [`quanttide-tutorial-of-social-media`](https://github.com/quanttide/quanttide-tutorial-of-social-media)

- [ ] `media/wechat.md`

#### 组织管理 → [`quanttide-tutorial-of-organization-management`](https://github.com/quanttide/quanttide-tutorial-of-organization-management)

- [ ] `org/culture/how.md`
- [ ] `org/culture/index.md`
- [ ] `org/founder-dependency.md`
- [ ] `org/index.md`
- [ ] `org/mechanism-design.md`

#### 开源管理 → [`quanttide-tutorial-of-open-source`](https://github.com/quanttide/quanttide-tutorial-of-open-source)

- [ ] `share/license.md`

#### 标准化 → **【待建教程仓库】**

- [ ] `stdn/bylaw.md`
- [ ] `stdn/index.md`

#### 战略管理 → [`quanttide-tutorial-of-strategy-management`](https://github.com/quanttide/quanttide-tutorial-of-strategy-management)

- [ ] `strategy/build-in-public.md`
- [ ] `strategy/business-model.md`
- [ ] `strategy/challenges.md`
- [ ] `strategy/competence.md`
- [ ] `strategy/governance-layer.md`
- [ ] `strategy/rule-of-law.md`

#### 写作管理 → [`quanttide-tutorial-of-narrative-engineering`](https://github.com/quanttide/quanttide-tutorial-of-narrative-engineering)

- [ ] `write/brochure.md`
- [ ] `write/bylaw.md`
- [ ] `write/index.md`

### 留在公司教程

共 24 篇，都是主体性的内容：

| 文件 | 为什么留 |
|:--|:--|
| `index.md` | 教程入口、三层文档说明 |
| `intro/index.md` | 新人快速入门 |
| `appendix/definitions.md` | 本公司的定义 |
| `org/company-representative.md` | 法定代表人制度——公司特有的治理安排 |
| `market/index.md` | 市场营销——暂无对应领域教程，先留 |
| `qtdata/`（9 篇） | 量潮数据业务线怎么跑 |
| `qtclass/`（3 篇） | 量潮课堂业务线怎么跑 |
| `qtcloud/`（1 篇） | 量潮云业务线怎么跑 |
| `qtconsult/`（3 篇） | 量潮咨询业务线怎么跑 |
| `qtcrowd/`（1 篇） | 量潮众包业务线怎么跑 |
| `qtrecurit/`（2 篇） | 量潮招聘业务线怎么跑 |

### 前置条件：两个领域还没有教程仓库

| 领域 | 需建仓库 | 承接内容 |
|:--|:--|:--|
| 商务拓展 | `quanttide-tutorial-of-business-development` | `business/quotation.md` |
| 议事管理 | `quanttide-tutorial-of-deliberation-management` | `delib/`（2 篇） |

两处未定：

- **标准化**（`stdn/`，2 篇）无对应领域，目标待定——放通识层 `quanttide-tutorial-of-readme`，还是先留本仓库
- **`connect/README.md`** 是 3 行占位，与 `connect/index.md` 重复，迁出时应直接删除而不是搬运

### 迁出后的收口动作

每迁完一章，做四件事：

1. 内容写进目标领域教程仓库，按 `docs/` 的写法组织，不复述公司口径
2. 本仓库删原文件，`myst.yml` 目录同步
3. 需要保留的公司口径，改写成指向领域教程的指针段落
4. 本仓库 `CHANGELOG.md` 记一条，注明迁往何处

### 迁出后的公司教程长什么样

```text
default/company/          # 量潮科技工作教程——只讲"这家公司"
├── index.md
├── intro/                # 新人入门
├── appendix/             # 定义
├── market/               # 市场营销（待定去向）
├── org/                  # 只剩 company-representative.md
└── qtdata|qtclass|qtcloud|qtconsult|qtcrowd|qtrecurit/   # 业务线
```

领域类章节（`agent/`、`asset/`、`connect/`、`delib/`、`devops/`、`finance/`、`media/`、`org/`、`share/`、`stdn/`、`strategy/`、`write/`、`business/`）全部腾空。

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
