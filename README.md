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

## 发布（真开源，兑现官网"开源"字样）

> 2026-10-03 现状：官网已按"**不挂不存在的开源物**"红线去掉"开源"二字（口径：「我们的 Skill chensibo-vibe · 整理发布中」）。
> 本包今晚整理就绪（`git init` + 首次提交），**推送公开仓后**按下面第 3 步把"开源"字样加回官网。

1. **CNB 公开仓（首选）**：在 <https://cnb.cool> 建 `chensibo/chensibo-vibe` 仓库（创建时选 **Public**；
   若当前账号/组织不支持公开仓，见第 2 步），然后：

   ```bash
   cd chensibo-vibe
   git remote add origin https://cnb.cool/chensibo/chensibo-vibe.git
   git push -u origin main
   ```

2. **GitHub 公开仓（备选）**：`gh repo create chensibo/chensibo-vibe --public --source=. --push`
   （或网页新建 public 仓后 push）。

3. **推送成功后回官网加回"开源"字样**（3 处 + 底注，去掉"整理发布中"限定）：
   - `docs/glossary.md`：description、AI 小课堂段、四要素尾注、FAQ Q2、FAQ Q5、CTA note
   - `docs/.vitepress/theme/components/GlossaryExplorer.vue` 底注
   - 并给每处补仓库链接 `<https://cnb.cool/chensibo/chensibo-vibe>`（或 GitHub 地址）
   - **同时删掉 `scripts/assert-narrative.mjs` 禁词表里的 `开源 Skill` / `MIT 开源` 两条**
     （注释已写明"推仓后移除"），删完跑一遍断言 8/8 即收口。

## 维护（与官网同源）

术语真源在官网仓库 `chensibo/docs-site`：

- 数据本体：`docs/.vitepress/theme/components/GlossaryExplorer.vue` 的 `groups`（26 条）
- 页面文案：`docs/glossary.md`

改术语的正确顺序：**先改官网 → 跑断言 → 用同样的抽取逻辑更新本包 `references/glossary-data.json` → 双边同步提交**。
（2026-10-03 首版即按此流程从站上程序化抽取，一字未改。）

## License

MIT，见 `LICENSE`。版权：2026 南京市沉思波网络科技有限责任公司。
