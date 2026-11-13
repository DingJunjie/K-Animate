# infp-growth · INFP 成长指南

MBTI 成长系列第 1 部。模式 `knowledge`，载体 `web`，画幅 9:16（主）+ 16:9。

## 文件

| 路径 | 说明 |
| --- | --- |
| `prompt/brief.md` | 任务书 |
| `research/sources.md` | 依据与知识边界 |
| `storyboard/outline-v2.md`、`materials-v2.md` | v2 大纲与材料方向 |
| `storyboard/storyboard-v2.md` | v2 分镜与字幕（已确认） |
| `storyboard/storyboard.md`、`src/v1.html` | v1（保留作对照） |
| `src/v2.html` | v2 实现，11 段已全部写完 |
| `src/frames-v2.html`、`src/anim-v2-s6.html` | 风格帧与段 6 动画原型（参考） |

## 状态

- 已完成：v2 全片 11 段画面与字幕（9:16）；音频载入、校准、`renderAt(t)`、`window.ready`（Promise）、`?capture&t=`。
- 待校准：锚点来自响度分析（±2s），未实际对齐音频，不声称已卡点。
- 待检查：16:9 只做了比例适配，未实际播放检查。
- 待核实：微信撤回时限、千克原器漂移、Beebe 原型名、磁偏角、迎风换舷。核实前用保守写法或只放角标。
- 未做：视频导出。

入口按版本命名（`v1.html`、`v2.html`），不使用 `index.html`；当前版本为 v2。

## 资产与许可

| 资产 | 来源 | 许可 | 入库 |
| --- | --- | --- | --- |
| `assets/A Careful Name.mp3` | 用户用 Suno 生成 | 待确认 Suno 会员条款下的使用权 | 否（`.gitignore` 排除） |

## 外部依赖

无。字体使用系统字体回退（Noto Serif SC / Songti SC，IBM Plex Mono / Menlo），未接 CDN。

## 预览

```sh
python3 -m http.server 8000   # 在仓库根目录
# 打开 http://localhost:8000/projects/infp-growth/src/v2.html
```

音频需在页面里点「载入音频」从本地选择。