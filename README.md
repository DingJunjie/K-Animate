# 知识动画工坊

使用 Web 技术制作可持续产出的知识动画。以知识点组织完整作品，以共享目录积累制作能力。

## 目录

```text
prompt/                      全局制作方法（分层，见 prompt/README.md）
  core/                      所有模式、所有载体通用的方法（含画幅）
  modes/                     内容维度：knowledge、song
  media/                     载体维度：web、ai-video
  references/                案例与历史存档，不作为规则
  TODO.md                    全局制作待办
projects/                    每个知识点一个独立子项目
  dice-probability/           首个项目：骰子与概率
    prompt/                  本片任务书与提示词
    research/                事实核查、来源、计算
    storyboard/              分镜与旁白
    assets/                  本片图片、字体、模型、音频
    src/                     页面和动画源码
    output/                  截帧、视频等生成结果（不入库）
shared/                      经实际项目验证的共享组件、样式、工具
tools/                       预览、截帧与视频合成工具
```

一个作品所需的提示词、依据、资产和代码放在一起，便于独立修改、归档和交付。顶层共享目录只收纳真正通用的部分；先在作品里实现，多个作品需要时再提取，避免过早建立复杂框架。

文件夹使用稳定的英文标识，中文名称写在项目 README 中。项目专属提示词引用全局模板与规则，只记录本片的主题、风格选择和例外。

## 制作流程

选题与核心问题 → 事实核查 → 分镜与旁白 → 短样片 → 完整动画 → 截帧与视频导出。

首支可运行样片为 [一段动画，如何诞生](projects/how-ai-animation-works/README.md)：32 秒字幕动画，解释 AI 编写 Web 动画的制作流程。[骰子与概率](projects/dice-probability/README.md) 保留为后续知识选题。具体待办见 [prompt/TODO.md](prompt/TODO.md)。

## 提示词入口

- [提示词体系](prompt/README.md)：分层说明与加载顺序（`core/` → `modes/` + `media/` → 项目任务书）。
- [动画导演](prompt/core/director.md)：通用入口。
- [通用工程约定](prompt/core/production.md)、[画幅与构图](prompt/core/framing.md)
- 模式：[知识](prompt/modes/knowledge.md)（含选题类别）、[歌曲](prompt/modes/song.md)
- 载体：[网页代码动画](prompt/media/web.md)、[AI 视频](prompt/media/ai-video.md)
- [初始参考提示词（历史存档）](prompt/references/knowledge-animation-original.md)：保留最初版本，不作为通用制作规则。

首片采用原生 ES Module、DOM、Canvas 与本地 Three.js，无需构建。后续根据制作需要评估视频框架，尚未引入 Remotion。

## 交互解析网页

[谁在行动？Agent / Skill / Tool](projects/agent-skill-explainer/README.md)：响应式概念指南，支持直接打开 HTML，无需 API 或构建。

## 动画导演体系

- [作品模式](prompt/README.md#作品模式)：knowledge、song-story、lyric-visual；concept-film 待有项目时建立。
- [段落卡与量化检查](prompt/core/segment-card.md)
- [《我不难过》企划](projects/i-am-not-sad/README.md)
