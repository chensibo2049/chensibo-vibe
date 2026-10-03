# chensibo-vibe

把想法变成能上线的产品——**先学会把需求说清楚**。

沉思波（南京市沉思波网络科技有限责任公司）的方法论 Skill：需求四要素体检 + 26 条 Vibe 术语对照，
内容与官网学习中心 <https://chensibo.cn/glossary.html> 同源，全部来自真实交付项目。

```
chensibo-vibe/
├── SKILL.md                     # Skill 主文件（角色 / 工作流 / 红线）
├── README.md                    # 本文件：用法、安装、发布、维护
├── LICENSE                      # MIT（随公开仓发布生效）
└── references/
    ├── glossary-data.json       # 26 条术语 · 4 组（人话解释 / 可以这样说 / 何时用）
    ├── brief-four-elements.md   # 需求四要素（定义 + 模板 + 示例，站内原文）
    ├── brief-check-rules.md     # 体检判定规则（正则 + 补全模板，取自站上 AI 小课堂工具）
    └── ai-speaking-three-points.md  # 跟 AI 说话三个要点（第 0 课原文）
```

## 能做什么

| 场景 | 输入 | 输出 |
| --- | --- | --- |
| 提需求 | "我想做个小程序让学生刷题" | 按四要素体检 → 缺项追问/代拟 → 一段可直接发给 Agent 的完整需求 |
| 说人话查词 | "鼠标放上去有点反应" | 术语「悬停反馈 Hover State」+「可以直接这样说：…」+ 使用场景 |
| 问术语 | "什么是骨架屏" | 人话解释（`plain`）+ 一句可复述的说法 |
| 教你跟 AI 说话 | 任意 | 三个要点：说结果不说实现 / 给参照物 / 小步走常验收 |

## 安装

**Claude Code / Claude 类 Agent（Skills 目录）**

```bash
# 项目级：随仓库分发
mkdir -p .claude/skills && cp -r chensibo-vibe .claude/skills/

# 用户级：全项目可用
mkdir -p ~/.claude/skills && cp -r chensibo-vibe ~/.claude/skills/
```

**其它 Agent 框架**：把整个目录当作一个 skill 包放入该框架的 skill 目录，
入口读 `SKILL.md`（frontmatter 的 `name` / `description` 用于自动触发），资料按需读 `references/`。

**只想拿数据**：`references/glossary-data.json` 单文件即可，MIT，可直接集成进你自己的 Agent。

## 仓库（已开源 · 2026-10-03）

**真实地址：<https://github.com/chensibo2049/chensibo-vibe>**（GitHub public，老板个人号推送；
匿名 `git ls-remote` HEAD `3a88dc279056491893c3c277d2eab7c1209cc6d7` 与本包首提交一致，HTTP 200，LICENSE MIT 可读）

```bash
git clone https://github.com/chensibo2049/chensibo-vibe.git
```

> ⚠️ 早期计划里的 CNB 地址 `cnb.cool/chensibo/chensibo-vibe` **不存在**（CNB 建仓 API 不可用，只有网页能建）——
> **一律使用上述 GitHub 地址**；若日后在 CNB 网页建镜像仓，再在此处追加。

### 开源状态闭环（官网 ↔ 仓库）

| 环节 | 状态 |
| --- | --- |
| 官网去掉"开源"字样（不挂不存在的东西） | ✅ 2026-10-03 白天，8 处，断言禁词防回潮 |
| Skill 包整理（SKILL.md + 4 references + LICENSE） | ✅ 首提交 `3a88dc2` |
| 推公开仓 | ✅ 墨衡推送 GitHub，ls-remote 同 hash 验证 |
| **官网加回"开源"+ 仓库链接** | ✅ 7 处（glossary 6 + GlossaryExplorer 底注），`release=20261003202352-8d48399` |
| 删断言禁词 2 条 + 必含链接（htmlMust 源码检查） | ✅ 断言 8/8 PASS |

## 维护（与官网同源）

术语真源在官网仓库 `chensibo/docs-site`：

- 数据本体：`docs/.vitepress/theme/components/GlossaryExplorer.vue` 的 `groups`（26 条）
- 页面文案：`docs/glossary.md`

改术语的正确顺序：**先改官网 → 跑断言 → 用同样的抽取逻辑更新本包 `references/glossary-data.json` → 双边同步提交**。
（2026-10-03 首版即按此流程从站上程序化抽取，一字未改。）

## License

MIT，见 `LICENSE`。版权：2026 南京市沉思波网络科技有限责任公司。
