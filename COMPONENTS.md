# 量潮课堂 · 组件规格书

> v0.12 · Material Design 设计系统 · 海岸配色
>
> 本文档描述量潮课堂 LMS 系统的组件体系，供前端工程化实现时参考。
> 每个组件定义：名称、CSS 类、用途、变体、状态、插槽。

---

## 设计 Token

```css
/* —— 海岸配色 —— */
--primary:        #268BFF;   /* Ocean Blue · 品牌主色 */
--primary-light:  #5EBFFF;   /* Hover 态 */
--primary-dark:   #0F3D66;   /* Deep Ocean · Logo/标题 */
--secondary:      #6CCEFF;   /* Sky Blue · 辅助 */
--secondary-light:#E3EDF5;   /* 浅边框底色 */
--accent:         #3ED3C5;   /* Sea Cyan · 潮汐/增长 */
--surface:        #F7FBFD;   /* 海雾白 · 页面背景 */
--surface-container: #FFFFFF; /* 卡片白 */
--on-surface:     #1B2A3A;   /* 深海灰 · 一级文字 */
--on-surface-variant: #5D7188; /* 二级文字 */
--outline:        #E3EDF5;   /* 海雾边框 */
--error:          #F25F5C;   /* 珊瑚红 */
--success:        #20C997;   /* 海水绿 */
--warning:        #F5A623;   /* 夕阳橙 */

/* —— Elevation (Material 规范) —— */
--elev-1: 0 1px 2px rgba(0,0,0,.08), 0 1px 3px rgba(0,0,0,.04);
--elev-2: 0 1px 2px rgba(0,0,0,.10), 0 2px 6px rgba(0,0,0,.06);
--elev-3: 0 1px 3px rgba(0,0,0,.12), 0 4px 8px rgba(0,0,0,.06);
--elev-4: 0 2px 3px rgba(0,0,0,.12), 0 6px 10px rgba(0,0,0,.08);

/* —— Typography (Material Type Scale) —— */
--fs-h4:34px;--fs-h5:24px;--fs-h6:20px;
--fs-sub1:16px;--fs-body1:14px;--fs-body2:12px;--fs-caption:11px;

/* —— Shape —— */
--radius-sm:8px;--radius-md:12px;--radius-lg:16px;--radius-full:9999px;

/* —— Spacing (8px grid) —— */
--sp-1:4px;--sp-2:8px;--sp-3:12px;--sp-4:16px;
--sp-5:20px;--sp-6:24px;--sp-8:32px;--sp-12:48px;
```

---

## 组件总览

| 类型 | 数量 | 组件 |
|------|------|------|
| 导航 | 2 | AppBar, SideNav |
| 布局 | 4 | PageHeader, Section, TwoCol, CardGrid |
| 内容 | 10 | CourseCard, Badge, Button, StatCard, DataTable, StepBar, ModuleCard, Pipeline, Timeline, FormField |

---

## 一、导航组件

### 1. AppBar · 顶部导航栏

| 属性 | 值 |
|------|-----|
| CSS 类 | `.appbar` |
| 高度 | 56px |
| 背景 | `var(--primary)` |
| 文字 | `var(--on-primary)` |
| Elevation | 4dp |

**子元素：**
- `.logo` — Logo / 系统名称，点击返回首页
- `.switch-group` — 视图切换按钮组（前台 / 后台）
- `.meta` — 右侧元信息（版本号等）

**状态：** 无特殊状态，始终置顶。

---

### 2. SideNav · 侧边导航

| 属性 | 值 |
|------|-----|
| CSS 类 | `.sidenav` |
| 宽度 | 220px |
| 背景 | `var(--surface-container)` |

**子元素：**
- `.nav-group` — 导航分组
- `.nav-label` — 分组标题，可点击折叠，含 `.arr` 箭头
- `.nav-kids` — 子项容器，折叠态加 `.folded`（max-height:0）
- `.nav-item` — 导航项，子项加 `.sub`（缩进），占位项加 `.placeholder`

**状态：**
- `:hover` — 浅蓝背景
- `.active` — 深蓝背景 + 主色文字
- `.folded` — 折叠隐藏

**变体：**
- `.sub` — 子级缩进 32px
- `.placeholder` — 灰色不可点击

---

## 二、布局组件

### 3. PageHeader · 页面标题区

| 属性 | 值 |
|------|-----|
| CSS 类 | `.page-header` |
| 对齐 | 居中 |
| 下边距 | `var(--sp-12)` |

**子元素：**
- `h1` — 页面标题
- `.desc` — 描述文字（最大宽 560px 居中）

---

### 4. Section · 内容分区

| 属性 | 值 |
|------|-----|
| CSS 类 | `.section` |
| 下边距 | `var(--sp-6)` |

**子元素：**
- `.section-hd` — 标题栏（flex，标题+操作按钮左右分布）
- `.section-hd h3` — 分区标题
- `.section-body` — 内容区

---

### 5. TwoCol · 两栏布局

| 属性 | 值 |
|------|-----|
| CSS 类 | `.twocol` |
| 间距 | `var(--sp-6)` |

**子元素：**
- 直接子元素均分宽度（flex:1）
- `.side` — 固定 280px 侧栏

---

### 6. CardGrid · 卡片网格

| 属性 | 值 |
|------|-----|
| CSS 类 | `.card-grid` |
| 最大宽 | 720px 居中 |
| 排列 | 纵向，间距 `var(--sp-3)` |

---

## 三、内容组件

### 7. CourseCard · 课程卡片

| 属性 | 值 |
|------|-----|
| CSS 类 | `.course-card` |
| 布局 | 横向 flex，圆角 12px |
| Elevation | 1dp，hover 升到 3dp |

**子元素：**
- `.cc-num` — 编号圆（48px，默认灰色，`.active-card` 下变主色）
- `.cc-info` — 课程信息
- `.cc-name` — 课程名
- `.cc-desc` — 课程描述

**状态：**
- 默认 — 白色背景，hover 右移 4px
- `.active-card` — 编号圆变主色，可点击进入
- `.coming` — 半透明，不可点击，hover 无反馈

**搭配：** 放在 `.card-grid` 中使用。

---

### 8. Badge · 状态标签

| 属性 | 值 |
|------|-----|
| CSS 类 | `.badge` |
| 形状 | 圆角胶囊 |

**变体：**
| 变体 | 背景 | 用途 |
|------|------|------|
| `.beginner` | 浅蓝 | 入门课程 |
| `.intermediate` | 浅靛 | 进阶课程 |
| `.advanced` | 浅橙 | 实战课程 |
| `.capstone` | 浅红 | 综合作业 |
| `.draft` | 浅橙 | 草稿状态 |
| `.review` | 浅蓝 | 待审批 |
| `.active-status` | 浅绿 | 进行中 |
| `.done` | 浅紫 | 已完成 |

---

### 9. Button · 按钮

| 属性 | 值 |
|------|-----|
| CSS 类 | `.btn` |
| 圆角 | 8px |
| 字号 | 14px |

**变体：**
| 变体 | CSS 类 | 用途 |
|------|--------|------|
| Filled | `.btn-filled` | 主操作（主色背景） |
| Tonal | `.btn-tonal` | 次要操作（浅色背景） |
| Outlined | `.btn-outlined` | 辅助操作（边框） |
| Text | `.btn-text` | 文字按钮（无背景） |

**尺寸：**
- 默认 — 10px 24px
- `.btn-sm` — 6px 14px（表格内操作）
- `.btn-lg` — 14px 32px（Hero 区 CTA）

**状态：** hover 变浅/加阴影，active 变深，focus 加 outline。

---

### 10. StatCard · 统计卡片

| 属性 | 值 |
|------|-----|
| CSS 类 | `.stat-card` |
| 布局 | 均分宽度，横向排列 |
| 容器 | `.stat-row`（flex 容器） |

**子元素：**
- `.num` — 数字（32px 粗体）
- `.label` — 标签（12px 灰色）

---

### 11. DataTable · 数据表格

| 属性 | 值 |
|------|-----|
| CSS 类 | `.datatable` |
| 字号 | 12px |

**子元素：**
- `th` — 表头（灰色文字，2px 底线）
- `td` — 单元格（13px 内边距）
- `tr:hover td` — 行 hover 浅蓝背景

---

### 12. StepBar · 横向步骤条

| 属性 | 值 |
|------|-----|
| CSS 类 | `.stepbar` |
| 布局 | 居中 flex，白色卡片 |

**子元素：**
- `.step` — 步骤容器（可点击）
- `.dot` — 步骤圆点（40px，默认灰色）
- `.label` — 步骤名称
- `.line` — 连接线（28px 宽）

**状态：**
- `.done` — 绿色 + ✓ 图标
- `.current` — 主色 + 外发光
- `.final` — 浅橙（大作业专用）

---

### 13. ModuleCard · 模块内容卡片

| 属性 | 值 |
|------|-----|
| CSS 类 | `.module-card` |
| 布局 | 横向 flex |

**子元素：**
- `.mod-num` — 编号圆（44px）
- `.mod-info` — 模块信息
- `.mod-title` — 模块标题
- `.mod-desc` — 模块描述

**状态：**
- 默认 — 白色边框
- `.done` — 左侧绿色边框 + 编号圆变绿
- `.current` — 主色边框 + 编号圆变主色

---

### 14. Pipeline · 流程条

| 属性 | 值 |
|------|-----|
| CSS 类 | `.pipeline` |
| 布局 | 横向均分 |

**子元素：**
- `.stage` — 阶段节点，之间用 `→` 连接
- `.icon` — 图标圆（44px）
- `.name` — 阶段名称（12px 粗体）
- `.hint` — 阶段说明（11px 灰色）

---

### 15. Timeline · 时间线

| 属性 | 值 |
|------|-----|
| CSS 类 | `.timeline` |
| 左边框 | 2px 实线 |

**子元素：**
- `.timeline-item` — 时间线节点
- `.ts` — 时间戳
- `.event` — 事件描述

**装饰：** 每个节点左侧有 12px 圆点 + 主色边框。

---

### 16. FormField · 表单输入

| 属性 | 值 |
|------|-----|
| CSS 类 | `.form-group` |
| 下边距 | `var(--sp-4)` |

**子元素：**
- `label` — 标签（12px 粗体）
- `input / textarea / select` — 输入控件

**状态：**
- 默认 — 浅灰边框
- `:focus` — 主色边框 + 外发光

**布局变体：** `.form-row` — 两栏并排表单。

---

## 页面模板

### 前台：课程列表页

```
PageHeader
  └─ h1 + .desc
CardGrid
  └─ CourseCard × 5
```

### 前台：课程内页（每门课复用）

```
back-link (← 返回课程列表)
StepBar (仅模块页显示)
course-hero (课程首页)
module-panel × N (模块内容)
```

### 后台：LMS 管理

```
Section · 概览
  └─ stat-row
      └─ StatCard × 4
Section · 课题管理
  └─ DataTable
Section · 审批中心
  └─ TwoCol
      ├─ Timeline
      └─ FormField × 2 + Button
Section · 双创项目管理
  └─ Pipeline (5 阶段)
```

---

## 工程化建议

1. **CSS 变量** — 所有颜色/间距/字号已抽到 `:root`，改主题只需换变量值
2. **组件命名** — 遵循 BEM 变体（`.component-name--variant` 可进一步拆分）
3. **状态管理** — 当前用 CSS class 切换，工程化后可用 data-attr 或 JS 框架状态
4. **响应式** — 当前桌面端优先，移动端需补充 breakpoint（建议 768px/1024px）
5. **框架迁移** — 12 个内容组件 + 4 个布局组件可直接映射到 React/Vue 组件