# PROJECT.md · 知识动画工坊速览

供新接手的 AI 或协作者快速了解项目。详细说明见 [README.md](README.md) 与 [prompt/README.md](prompt/README.md)。

## 项目是什么

用 Web 技术（HTML/CSS、Canvas 2D，必要时 Three.js）制作**自动播放的动画短片**。观众点击播放后完整观看，无须滚动或点击推进；网页只是播放器。

每部作品由三个独立维度描述：**模式**（知识、歌曲等，决定讲什么、怎么组织）、**载体**（网页代码动画、AI 视频，决定怎么做出来）、**画幅**（16:9、9:16 等）。所有作品共享一套通用方法，各模式、各载体只补充自己的差异。

## 核心原则

- 画面的状态变化直接参与表达，不只是给文字做入场装饰。
- 不预设风格：黑底、金色、衬线、粒子等都由单片任务书决定。
- 参考只提取方法，不搬运其道具、故事和构图。
- 重复内容（如歌曲副歌）不复制画面，必须有可见递进。
- 节奏来自轻重、快慢与变化，不靠统一加速或全片弹字。
- 无构建：直接打开 HTML 或用本地 HTTP 服务即可预览。
- 先在作品内实现，多个作品需要时再提取到 `shared/`。
- 如实说明未完成部分：音频卡点、视频导出等未实现时不声称已实现。

## 目录

```text
PROJECT.md                     本文件：项目速览
README.md                      项目说明与入口链接
prompt/                        创作方法（三层体系）
  README.md                    分层说明、加载顺序、任务书模板
  core/                        第一层：所有模式通用
    director.md                入口：角色、作品形式、交付边界、层级规则
    workflow.md                6 步制作流程与复盘顺序
    visual-design.md           构图、色彩、形态、光影、字体
    motion-rhythm.md           状态变化链、动作、衔接、节奏、文字动效
    audience.md                注意力主次、文字分工、停留与表达边界
    segment-card.md            段落卡格式、快速评分、密度参考（与载体无关）
    framing.md                 画幅、安全区、多画幅策略
    production.md              所有载体通用：目录、载体选择、资产许可、声音授权
  modes/                       第二层 · 内容维度
    knowledge.md               知识片：理解主题、拆解步骤、事实依据、选题类别
    song.md                    歌曲片：歌词与音频分析、母题、重复递进
  media/                       第二层 · 载体维度
    web.md                     网页代码动画：时间轴、锚点、截帧接口、校准模式
    ai-video.md                AI 视频：镜头表、提示词结构、一致性、后期分工
  references/                  案例与历史存档，不作为规则
  TODO.md                      全局待办
projects/<name>/               每部作品一个独立目录
  prompt/brief.md              第三层：单片任务书（声明模式）
  research/                    依据与来源
  storyboard/                  分镜
  assets/                      本片资产
  src/index.html               实现入口
  output/                      截帧与视频（不入库）
shared/                        经验证的共享代码（目前为空）
tools/                         预览、截帧、视频合成工具（目前为空）
```

## 提示词加载顺序

1. `prompt/core/director.md`，再按需读 `core/` 其余文件。
2. 任务书声明的模式与载体文件：`prompt/modes/<模式>.md`、`prompt/media/<载体>.md`。
3. 项目任务书：`projects/<name>/prompt/brief.md`。

归属判断：对所有模式、所有载体成立 → `core/`；只对某一模式成立 → `modes/`；只对某一载体成立 → `media/`；只对某一部作品成立 → 任务书。下层只补充、收窄；要推翻上层时在任务书写明「例外」及理由。

## 作品模式

| 模式 | 优先 | 方法文件 |
| --- | --- | --- |
| `knowledge` | 事实与理解，画面证明概念 | `modes/knowledge.md` |
| `song-story` | 情绪、歌词与角色弧线 | `modes/song.md` |
| `lyric-visual` | 歌词与视觉节拍，允许抽象 | `modes/song.md` |
| `concept-film` | 主题与视觉隐喻 | 暂未建立 |

## 当前作品

| 目录 | 名称 | 模式 | 状态 |
| --- | --- | --- | --- |
| `how-ai-animation-works` | 一段动画，如何诞生 | knowledge | 32 秒字幕样片，可播放；无音轨 |
| `agent-skill-explainer` | 谁在行动？Agent / Skill / Tool | 交互网页（独立探索） | 可用；计划改为自动短片 |
| `i-am-not-sad` | 《我不难过》歌曲动画 | song-story | 旧版草稿可播放；正在重建任务书与分镜，时间需按歌词时间戳校正 |
| `dice-probability` | 骰子与概率 | knowledge | 仅立项，无分镜与代码 |
| `infp-growth` | INFP 的成长路线（MBTI 系列第 1 部） | knowledge · web · 9:16 + 16:9 | 任务书、依据、分镜已完成；待写代码，音乐由用户用 Suno 生成 |

## 工程约定摘要（web 载体）

- 画布尺寸按任务书声明的画幅；统一时间轴，每帧是时间 t 的确定结果；随机使用固定种子。
- 段落以锚点表组织，段内按进度 p 计算；载入音频后可用校准模式重写锚点。
- 暴露 `window.renderAt(t)` 与 `window.ready`（资源就绪的 Promise）。
- `?capture&t=秒数`：隐藏控件、停止播放、定位到指定时间，用于截帧。
- 有音轨时以音频时间为主时钟；未授权音频不入库，仅本地载入。

## 预览

```sh
# 在仓库根目录
python3 -m http.server 8000
# 打开 http://localhost:8000/projects/<name>/src/
```

## 给 AI 的工作要求

- 开始前先读本文件、`prompt/README.md`、目标项目的 README 与 `prompt/brief.md`。
- 歌曲作品的段落时间必须来自歌词时间戳或实际音频，不自行估算。
- 按本轮评审重点交付，不擅自扩大为整片重写。
- 交付时写明已完成与未完成的部分。