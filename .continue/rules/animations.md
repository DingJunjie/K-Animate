---
description: 在 Animations 仓库里制作或修改动画作品时适用，涵盖开工前阅读、编辑粒度、确认节点和复盘方式。
alwaysApply: true
---

1. 开工前先读 PROJECT.md、prompt/README.md、目标项目的 README、prompt/brief.md 和 review.md（如有），以及任务书声明的 modes/ 与 media/ 文件。
2. 单次写入或编辑不超过 50 行；长文件先建骨架并留占位符，再分批填充。调用 create_new_file 必须带 contents，调用 multi_edit 必须带 edits。
3. 看不到导出的图片时要直说，只报告「文件已生成」，不声称画面正确；请用户贴截图确认。
4. 立项第 0 步先确认观众画像与音乐要求（节拍、BPM、风格），再定核心观点。
5. 需要用户确认：观众、核心观点、材料方向、风格帧、字幕初稿、一个关键段动画。其余各段由 AI 执行，每完成 2–3 段交一组关键帧。
6. 未核实的事实不进正片；先核实再写钩子，核实不了时告诉用户，由用户决定是降级还是协助核实。
7. 每部完成后，把用户反馈整理成 projects/<name>/review.md，能通用的经验再提到 prompt/ 对应层级。