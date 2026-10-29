---
name: 飞红 App
version: 1.0.0
description: 中文生活方式社区移动端应用，单文件零依赖，仿小红书信息架构
colors:
  primary: "#FF2442"
  primary-press: "#E51D38"
  primary-disabled: "#FFC2CB"
  primary-soft: "#FFE8EC"
  star: "#FFB400"
  link: "#3B5BDB"
  link-bg: "#F2F5FF"
  text-1: "#1A1A1A"
  text-2: "#2B2B2B"
  text-3: "#999999"
  text-4: "#C0C0C0"
  divider: "#F0F0F0"
  fill: "#F4F4F6"
  bg: "#FFFFFF"
  bg-page: "#ECEFF3"
  mask: "rgba(0,0,0,0.42)"
  toast: "rgba(0,0,0,0.78)"
typography:
  note-title:
    fontSize: "18px"
    lineHeight: "1.4"
    fontWeight: 700
  card-title:
    fontSize: "13.5px"
    lineHeight: "1.35"
    fontWeight: 500
  body:
    fontSize: "15px"
    lineHeight: "1.75"
    fontWeight: 400
  tab:
    fontSize: "16px"
    fontWeight: 500
  caption:
    fontSize: "12px"
    fontWeight: 400
  micro:
    fontSize: "11px"
    fontWeight: 400
rounded:
  card: "10px"
  cover: "12px"
  button: "9px"
  pill: "18px"
  chip: "6px"
  avatar: "50%"
spacing:
  page-x: "14px"
  feed-gap: "8px"
  card-inner: "9px"
  section: "14px"
  tabbar-h: "52px"
motion:
  fade: "300ms"
  slide-in: "220ms"
  pop: "300ms"
  easing: "cubic-bezier(0.4, 0, 0.2, 1)"
components:
  card:
    background: "{colors.bg}"
    rounded: "{rounded.card}"
    borderWidth: 0
    boxShadow: none
  card-title:
    color: "{colors.text-1}"
    font: "{typography.card-title}"
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "#FFFFFF"
    rounded: "{rounded.button}"
    font: "{typography.card-title}"
  button-follow:
    backgroundColor: "transparent"
    borderColor: "{colors.primary}"
    textColor: "{colors.primary}"
    rounded: "{rounded.pill}"
  input:
    backgroundColor: "{colors.fill}"
    borderWidth: 0
    rounded: "{rounded.pill}"
    textColor: "{colors.text-1}"
  tag-chip:
    backgroundColor: "{colors.link-bg}"
    textColor: "{colors.link}"
    rounded: "{rounded.chip}"
---

## Overview

飞红是中文生活方式社区 App（内容形态对标小红书）：双列瀑布流发现、图文笔记详情、发布、消息、个人主页五块。

设计气质是**安静的底子 + 单一强调色**。页面本身几乎全白，只靠留白、圆角和字号层级区分结构；品牌红只出现在真正需要「一指点击的位置」——主按钮、点赞、当前 tab 指示条、未读角标。整屏红色面积控制在 10% 以内，超过就不再像社区，像促销页。

一条铁律：**不用阴影做层级，用留白和圆角**。App 里唯一允许的阴影是发布按钮的红色外发光，用来把它从底部栏里托起来。

## Colors

- **Primary `#FF2442`**：品牌红。只用于主按钮、点赞态、当前 tab 下划线、未读角标、输入框聚焦边。**禁止**用作大面积背景或页面底色。
- **Star `#FFB400`**：收藏态专用，与点赞红严格区分，避免两个动作看起来是同一件事。
- **Link `#3B5BDB` + `#F2F5FF`**：话题标签。蓝色是社区里唯一允许出现的第三种色相，因为标签必须和正文区分开。
- **Text 四级**：`#1A1A1A` 标题与正文主体 → `#2B2B2B` 长文正文 → `#999999` 作者名、计数、辅助说明 → `#C0C0C0` 占位符、时间戳、禁用。
- **Divider `#F0F0F0`**：0.5px 细线，只用于顶部栏、底部栏、输入区。卡片之间**不加线**，靠 8px 间距分隔。
- **Fill `#F4F4F6`**：所有无边框输入框、次级底色、空态占位。
- 封面图上的浮层文字用 `rgba(0,0,0,0.42)` + 模糊，绝不用纯白遮罩。

## Typography

字号阶梯只有四档，同屏出现超过三档就是错：

| 层级 | 字号/行高 | 字重 | 用途 |
|---|---|---|---|
| note-title | 18 / 1.4 | 700 | 笔记详情正文标题 |
| card-title | 13.5 / 1.35 | 500 | 瀑布流卡片标题，最多两行截断 |
| body | 15 / 1.75 | 400 | 笔记正文，`white-space: pre-wrap` 保留作者换行 |
| caption / micro | 12 / 11 | 400 | 作者名、点赞数、时间、空态提示 |

正文行高固定 1.75，这是中文长文可读性的下限，不要为了塞更多内容压到 1.5。卡片标题用 `-webkit-line-clamp: 2` 截断，不做省略号手写。

## Layout

- 页面左右边距 **14px**，瀑布流两列间隙 **8px**，卡片内边距 **9px**。
- 瀑布流不做等高对齐：封面用 `padding-top` 百分比撑出不同的宽高比（1.0–1.45），参差本身就是信息密度的一部分。分列算法按累计高度取较短列，不要按奇偶交替（会一高一低两条长蛇）。
- 底部 tab 栏高 **52px**，并加 `env(safe-area-inset-bottom)`；页面内容底部预留 16–26px，避免最后一个卡片贴住 tab。
- 详情页是整页覆盖层，滑入 220ms，不做半屏抽屉。
- 桌面端把容器锁在 **430px** 并居中加投影，模拟手机；430px 以下铺满。

## Elevation & Depth

只有三层，全部靠 z-index 和留白，不靠阴影：

1. 内容层（0）：卡片、正文
2. 固定层（9–10）：顶部 tab、底部 tab 栏
3. 覆盖层（30+）：详情页、发布页、弹窗、toast

唯一允许的阴影：`0 3px 10px rgba(255,36,66,0.35)`，只给发布按钮。卡片、头像、输入框一律无阴影。

## Shapes

- 卡片 10px、详情大图 12px、主按钮 9px、胶囊 18px、话题 chip 6px、头像正圆。
- 圆角只有一个来源：`--r-*` 变量。不要在组件里写死像素。
- 不做异形裁切、不做斜切角，形状系统必须能被一句话复述。

## Components

- **卡片**：无边框、无阴影、圆角裁切；封面在下、标题在上两行、底部一行「头像 + 作者 + 点赞数」。点赞已赞时数字变红并加 `♥`，未赞用 `♡`。
- **关注按钮**：1px 红描边 + 红字 + 白底 + 胶囊；已关注转为灰边灰字，文案变「本人」或「已关注」。**不做红底**——关注是低优先动作，红底只留给发布。
- **输入**：无边框、`--c-fill` 底、胶囊圆角、placeholder 用 `--c-text-4`。
- **话题标签**：蓝字浅蓝底 chip，前置 `#`，可点击。
- **toast**：黑 78% 底、白字、圆角 10px，1.5s 自动消失，居中偏上。
- **空态**：居中、`--c-text-4`、13px、一句话说明 + 一句引导动作。

## Interaction

- 移动端**不做 hover**，只做 `:active`：卡片按下 `opacity: .85`，按钮按下 `transform: scale(.94)`。
- 三个标准动效：卡片入场 `fade + 上移 8px`（300ms）、详情页 `滑入`（220ms）、点赞 `scale 1 → 1.35 → 1`（300ms）。
- 所有动效只动 `transform` 和 `opacity`，不动 `width/height/top`，避免掉帧。
- 不做骨架屏，改用 300ms 淡入，成本更低且不闪。

## Do's and Don'ts

**Do**
- 所有颜色、圆角、间距都从 `:root` 变量取，改风格只改一处。
- 每个可点区域视觉可以小，但触摸区不小于 44×44（用 padding 撑开）。
- 长文保留作者的原始换行（`pre-wrap`），这是社区内容的语气。
- 图片上没有文字时，用 emoji 大字号 + 同色系渐变撑场，保证不裂图、不空白。

**Don't**
- 不用紫蓝渐变、不用 3D 立体、不用玻璃拟态——这些是「看起来像 AI 生成」的第一特征。
- 不用纯黑 `#000`，最深到 `#1A1A1A`。
- 不引入 UI 框架（Element Plus / Naive UI / shadcn）。本项目是单文件零依赖，任何组件库都会立刻破坏这个前提。
- 不用阴影叠加做卡片分层，不用超过两种强调色。
- 不在移动端做 hover 态，不写桌面断点的多列布局。
- 不把品牌红用在大面积背景上（>20% 屏占比）。

## 如何应用

改风格只改三处：`:root` 里的 `--c-*`（配色）、`--r-*`（圆角）、`--sp-*`（间距）。字号阶梯若改，必须整档改动（例如 13.5 → 14 要同步卡片标题与作者名），不允许单点微调。
