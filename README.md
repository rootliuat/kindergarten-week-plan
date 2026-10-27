# 幼儿园周计划教案 Skill

根据一份幼儿园周计划与园方 Word 模板，填写上午集体活动教案和下午体育游戏内容，保持原版式并另存新文件。

技能名称：`kindergarten-week-plan`。本仓库整理自 2026 年 8 月底创建的版本，首个发布版保留原有 Skill、写作指南及两个脚本的内容。

## 下载与安装

- [下载 .skill 包](https://github.com/rootliuat/kindergarten-week-plan/releases/latest/download/kindergarten-week-plan.skill)
- [查看完整 Skill](SKILL.md)
- [查看详细写作指南](references/writing-guide.md)

支持 `.skill` 导入的宿主可直接导入下载的文件。Codex 使用源码目录安装：将本仓库放入 `~/.codex/skills/kindergarten-week-plan/`，确保 `SKILL.md` 位于该目录根部，然后重新启动或刷新技能列表。Windows 默认目录为 `C:\Users\你的用户名\.codex\skills\kindergarten-week-plan\`。

也可以直接对 Agent 说：

```text
请安装 https://github.com/rootliuat/kindergarten-week-plan 中的 kindergarten-week-plan 技能。
```

脚本需要 Python 及 python-docx；已验证的直接依赖见 requirements.txt。在技能目录运行：

```shell
python -m pip install -r requirements.txt
```

## 使用示例

```text
使用 kindergarten-week-plan，根据这份周计划和完整备课本模板填写教案。
这是小班第 3 周，只填写星期二、星期四、星期五的上午与下午活动。
活动名称以首页为准，保持原表格和首页，另存为新 Word。
活动回顾留空，等活动结束后据实补充。
```

请提供周计划 `.docx`；如果文件没有完整的详细教案页面，还需提供认可的上午、下午参考模板。班级、周次、日期和目标星期应能从文档或用户说明中确认。

## 生成内容

| 类型 | 填写项目 | 主要篇幅要求 |
| --- | --- | --- |
| 上午集体活动 | 活动名称、目标、重难点、准备、过程 | 过程四个环节，总计不超过 300 字 |
| 下午户外体育游戏 | 活动名称、准备、指导要点、回顾 | 指导要点不超过 200 字；有事实依据的回顾 100 至 170 字 |

按小、中、大班和实际周次调整内容；小班入园适应支持逐周递进，活动目标仍以当天活动为核心。教师做法具体，幼儿行为可观察，避免空泛套话。

## 模板与事实约束

- 保留首页、行高、列宽、左侧标签与页面样式；内容单元格使用仿宋_GB2312 小四、固定 22 磅行距。
- 按星期匹配活动并交叉校验日期；首页五天有活动不代表要写五天全部详细教案。
- 缺页时先确认目标星期，使用用户认可的完整页面作为母版；不凭空重画园方表格。
- 活动回顾依据真实现场情况；尚未开展时默认留空，明确要求预写才使用预设口径。
- 默认另存 `原文件名_已填写.docx`，原件不覆盖。交付前检查页数、映射、字体和文字溢出，并渲染逐页查看。

## 脚本接口

```shell
python scripts/inspect_doc.py 输入.docx
python scripts/fill_cells.py 输入.docx spec.json 输出_已填写.docx
```

`spec.json` 示例，表格和行索引均从零开始，以检查器输出为准：

```json
[
  {"table": 1, "row": 1, "lines": ["1.能说出自己的标记。", "2.尝试按标记取放物品。"]}
]
```

默认内容列为 `col=1`。填表脚本拒绝输入输出同路径、首页 `table=0` 和越界单元格。内容生成、星期映射、页面复制和视觉验收属于 Agent 工作流，不由这两个脚本自动完成。

仓库仅分发通用规则与工具，不含教师原始材料、班级名单或示例教案。`.skill` 包保留原始四文件结构；README、依赖清单与 AGENTS.md 是本次补充的仓库维护文档。
