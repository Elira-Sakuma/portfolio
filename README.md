# Ellen Ye — Portfolio

> 游戏运营方向 · 个人作品集

以绝区零（Zenless Zone Zero）HUD 风格构建的全交互式个人作品集网页。从入口页的狙击瞄准动画进入内容主页，涵盖自我介绍、实习经历、能力雷达图、项目案例、热爱生活板块与滚动驱动视频运镜。

整个项目在 AI 辅助下从零搭建，涵盖动画设计、交互实现、视频运镜编排与 3D 建模，纯手写 HTML / CSS / JavaScript，零框架依赖。

---

## 快速开始

1. 下载或 clone 本仓库
2. 用浏览器打开 `index.html`（推荐 Chrome / Safari）
3. 点击页面中央角色，触发瞄准射击拉近动画，自动跳转至内容主页

视频与图片资源已打包在仓库中，无需额外依赖。

---

## 页面结构

```
index.html  ──  入口页（Loading 动画 + 狙击光标 + 点击瞄准射击拉近）
  │
  └── ecosystem.html  ──  内容主页
        ├── ABOUT ME — 自我介绍 + Device Panel 数据面板
        ├── EXPERIENCE — 三段实习经历（可点击跳转详细页）
        ├── ABILITIES — 个人能力雷达图
        ├── PROJECTS — 项目经历卡片
        │     ├── 美团达人内容成长 → meituan-creator.html
        │     ├── 美团兴趣POI内容运营 → meituan-poi.html
        │     └── 游戏发行拆解 → 绝区零3.1活动清单与目的深度拆解.html
        │           └── 飞书甘特图文档（外链）
        └── LIFE — 热爱生活板块
              ├── 4 张 ticket-card（运动/音乐/宠物/二次元）
              └── 滚动驱动视频运镜（4 段运镜 + 文字叠加 + HUD）
```

---

## 文件清单

### 核心页面

| 文件 | 说明 |
|------|------|
| `index.html` | 入口页 — Loading 动画 + 档案导入界面 + 点击瞄准射击拉近 |
| `ecosystem.html` | 内容主页 — 全部内容板块汇总 |
| `archive-intro.html` | 原始档案导入页（保留不动） |

### 实习详细页

| 文件 | 说明 |
|------|------|
| `meituan-creator.html` | 美团 — 达人内容成长 |
| `meituan-poi.html` | 美团 — 兴趣 POI 内容运营 |
| `trip.html` | 携程 — 定制游内容运营 |

### 游戏发行拆解系列

| 文件 | 说明 |
|------|------|
| `绝区零3.1活动清单与目的深度拆解.html` | 活动清单分类 + 目的深度拆解（含飞书甘特图外链） |


### LIFE 视频运镜 Demo

| 文件 | 说明 |
|------|------|
| `life-3d-demo.html` | 滚动驱动视频运镜独立演示页 |
| `life-recording.mp4` | 运镜视频素材（4 段运镜，~15s） |

---

## AI 辅助搭建过程

本项目从零开始，在 AI 辅助下逐步完成了以下工作：

### 动画与交互

- 入口页 Loading 动画、档案导入 tear-reveal 过渡、解码文字效果、狙击光标追踪
- 点击瞄准后的射击动画链：click-flash → screen-shake 后坐力 → scope-vignette 黑环收缩 → zoom-in 放大 → white-flash 白闪 → 跳转
- 内容主页的滚动驱动卡片揭示、跑马灯关键词滚动、能力雷达图 Canvas 渲染

### 视频运镜

- 原始方案基于 Three.js + GLB 3D 模型实现滚动驱动摄像机运镜（4 段夸张镜头）
- 因模型体积与迁移成本，改为滚动驱动 video.currentTime seek 方案：将滚动进度 0–100% 映射到视频时间线，requestAnimationFrame 逐帧 seek，实现上下滑动流畅控制
- 兼容 Safari 的 seek 解锁处理（play-pause unlock + IntersectionObserver 预加载 + seekable 范围检查）

### 3D 建模

- 使用 Meshy AI 生成 GLB 格式 3D 模型（猫耳耳机角色），导入 Three.js 场景
- 配置 4 段摄像机运镜参数（Dutch Portrait / Orbital Swoop / Low Hero / Spiral Dive），包含 FOV、位置、旋转、缓动曲线
- 搭建动态光影（主光/补光/轮廓光/底部光/顶光）、粒子系统、网格地面

### 页面集成

- 入口页与内容主页的过渡衔接（zoom-in → white flash → overlay fade out）
- 导航栏滚动高亮修复（getBoundingClientRect 替代 offsetTop + life-video-section 归属处理）
- LIFE 板块视频运镜集成至 ecosystem.html，含文字叠加切换、HUD 进度条、扫描线装饰

---

## 设计风格

- **配色**：绝区零黄 `#FFD93D` + 深黑 `#0A0A0A` + 霓虹青/紫点缀
- **字体**：Inter + Noto Sans SC + JetBrains Mono
- **视觉元素**：切角边框（clip-path）、CRT 扫描线、Glitch 故障效果、HUD 标记、粒子背景
- **交互**：滚动驱动动画、狙击光标、解码文字、跑马灯、卡片 hover 扫描

---

## 技术栈

- 纯 HTML / CSS / JavaScript（零框架依赖）
- CSS clip-path + animation
- IntersectionObserver + requestAnimationFrame
- Video currentTime seek（滚动驱动视频帧）
- Three.js + GLTFLoader（3D 方案原型阶段）
- SVG HUD 图形

---

## 作者

**Ellen Ye**

游戏运营方向 · 达人运营 · AI 内容工具赋能

---

> Built with passion for games and content.
