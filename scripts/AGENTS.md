# scripts/
> L2 | 父级: ../AGENTS.md

成员清单
- AGENTS.md：本模块成员地图与维护约定。
- inspect_doc.py：python-docx 只读检查器，输出正文日期、表格索引与模板完整性。
- fill_cells.py：python-docx 填表器，消费 JSON 单元格规格，设置仿宋_GB2312 12pt 和固定 22 磅行距并另存 DOCX。

职责边界：inspect_doc.py 提供结构索引，fill_cells.py 消费索引；活动文字、星期映射和页面复制由调用方按 SKILL.md 完成。保持原有四文件版本，发布整理不改变脚本行为。

[PROTOCOL]: 变更时更新此头部，然后检查 AGENTS.md
