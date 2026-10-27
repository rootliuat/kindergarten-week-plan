# kindergarten-week-plan - 幼儿园周计划备课本填写技能

Markdown + Python + python-docx 1.1.2

```text
kindergarten-week-plan/
|-- AGENTS.md                 仓库地图、维护约定与发布记录
|-- SKILL.md                  技能触发条件、模板识别与交付流程
|-- README.md                 安装、使用、依赖和下载说明
|-- requirements.txt          已验证的 Python 直接依赖
|-- .gitignore                排除缓存、虚拟环境和临时输出
|-- references/               教案语言、年龄差异与篇幅规则
|-- scripts/                  DOCX 结构检查与内容单元格写入
`-- dist/                     原始 .skill 分发包和 SHA-256 清单
```

## 职责与依赖

SKILL.md 编排工作流并按需读取 references/writing-guide.md。scripts/inspect_doc.py 只读检查模板，scripts/fill_cells.py 按人工或 Agent 生成的 JSON 规格填表。两者依赖 python-docx，不负责自动生成教案文字或复制完整页面。

## 维护约定

保留园方模板、首页和原件。修改脚本时同步 INPUT/OUTPUT/POS 文件头与模块 AGENTS.md；文件增删时同步本地图。源码维护与本机安装分开；只有明确要求时才安装或发布。重新发布前核对 .skill 包内四个文件与源码的 SHA-256；新增仓库说明文件不进入原始技能包。

## 变更记录

- 2026-10-27：整理为独立公开 GitHub 仓库；保留 2026-08-30 版技能四个文件及原始分发包，新增使用说明、依赖和模块地图。

[PROTOCOL]: 变更时更新此头部，然后检查 AGENTS.md
