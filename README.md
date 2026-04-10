# TVC Director · TVC 广告创意导演

[English](README_en.md)

从产品 brief 到电影级 TVC 关键帧——你的 AI 广告创意导演。

一个将 AI Agent 转化为 **TVC 广告创意导演** 的 Skill，覆盖电视广告和品牌广告的完整创意流程：从产品 brief 到可直接使用的 **Nano Banana Pro** 关键帧提示词和 **Seedance** Multi-Phase 视频脚本。

## 成品展示

### 汽车 TVC — 产品电影化拆解

https://github.com/user-attachments/assets/541055ed-d716-4087-86e2-a27d375282ed

### 香水 TVC — 品牌世界穿梭

https://github.com/user-attachments/assets/df2d51af-acc2-4f34-a228-8b35ea754345

## 两大核心能力

### 1. 产品电影化拆解（Cinematic Product Breakdown）

不是简单的 360° 旋转——而是多 Phase 的产品微电影：

- 零件悬浮拆解/精密组装动画
- 功能可视化：屏幕亮起、追踪框、数字跳动 00:00:00→04:00:00、传感器发光
- 材质微距：金属磨砂纹理、玻璃折射、碳纤维编织
- 精确到秒的运镜编排：极慢拆解 → 爆发旋转 → 悬浮凝视 → 俯冲穿越
- 光影叙事：低调影棚光、侧光勾勒轮廓、光随旋转流动

### 2. 品牌世界融合（Brand World Crosscut）

产品不只活在黑底摄影棚里——它活在品牌世界中：

- 户外相机 → 跳伞、潜水、滑雪、攀岩
- 奢侈腕表 → 赛车、帆船、正式晚宴
- 护肤品 → 晨光仪式、自然山泉、日出
- 运动鞋 → 城市跑酷、马拉松、雨中街道

TVC 在「产品特写」和「品牌世界使用场景」之间交叉剪辑，通过匹配剪辑无缝切换（滑雪者旋转 → 产品旋转）。

## 工作流程

```
"帮我做一条户外相机的30秒TVC"
        ↓
  Phase 0: 入口模式判断
  Phase 1: 需求拆解（产品/时长）
  Phase 2: TVC 创意构思（2-3 个方向 → 选择 → 完整创意方案）
  Phase 3: 画风确认（A-E）
  Phase 4: 资产图提示词（产品多视图、材质微距、品牌世界环境）
  Phase 5: 分镜关键帧提示词 + Seedance Multi-Phase 视频脚本
  Phase 6: 迭代优化
  Phase 7: 交付物整理
        ↓
  可直接复制使用的 Nano Banana Pro 提示词、
  Seedance 视频脚本和创意方案文档
```

## 安装

### Cursor

```bash
git clone https://github.com/Ethanxwang/tvc-director.git ~/.cursor/skills/tvc-director
```

### Claude Code

```bash
git clone https://github.com/Ethanxwang/tvc-director.git ~/.claude/skills/tvc-director
```

## 入口模式

| 模式 | 触发信号 | 说明 |
|------|---------|------|
| **A：完整 TVC 创意流** | "帮我做一条xx产品广告" | Brief → 创意 → 画风 → 资产 → 分镜 → 打包 |
| **B：快速资产/提示词** | "帮我做一个产品 Hero Shot" | 跳过创意阶段，直接生成资产或关键帧提示词 |
| **C：分镜转化** | 提供 TVC 分镜脚本 | 画风 → 资产 → 将分镜转化为关键帧提示词 |
| **D：迭代修正** | "这张产品图xx不对" | 定位问题并提供修正版提示词 |

## TVC 叙事模型

| 模型 | 名称 | 核心逻辑 |
|------|------|---------|
| A | 痛点-解决 | 痛点场景 → 产品拯救 |
| B | 产品电影化拆解 | 多 Phase 微电影逐步揭示卖点 |
| C | 品牌世界穿梭 | 使用场景 ↔ 产品特写交叉剪辑 |
| D | 生活方式融入 | 产品自然融入理想生活 |
| E | 情感锚点 | 情感故事，产品为载体 |
| F | 蒙太奇揭示 | 视觉奇观 → 产品揭示 |
| G | 前后对比 | 使用前后的强烈反差 |
| H | 品牌宣言 | 价值观驱动，产品收束 |

## 交付物

```
my-tvc-project/
├── concept.md                      # TVC 创意方案文档
├── storyboard.md                   # 分镜脚本（如有）
│
├── assets/                         # 产品资产图提示词（Nano Banana Pro）
│   └── prompts/
│       ├── product-multiview.md
│       ├── product-detail-01.md
│       ├── env-01-extreme-sports.md
│       └── ...
│
├── keyframes/                      # 分镜关键帧提示词（Nano Banana Pro）
│   └── prompts/
│       ├── grid-01-brand-world.md
│       ├── grid-02-product-world.md
│       ├── endframe.md
│       └── ...
│
└── video-scripts/                  # Multi-Phase 视频提示词（Seedance）
    ├── segment-01-brand-world.md
    ├── segment-02-product-breakdown.md
    └── ...
```

## 知识库

| 角色 | 文件 | 内容 | 使用阶段 |
|------|------|------|---------|
| 创意导演 | `creative.md` | 8 种 TVC 叙事模型、视觉美学设计、创意方案模板 + 2 个示例 | Phase 2 |
| 提示词工程师 | `prompts.md` | 6 层提示词结构、画风锚定词库 A-E、12 种 TVC 场景类型、构图范式 | Phase 3-4 |
| 分镜与视频 | `production.md` | 多宫格分镜、视频提示词语法、产品电影化拆解、品牌世界镜头 | Phase 5 |
| 输出与迭代 | `infra.md` | 输出格式模板、迭代调试指南（11 种常见失败模式） | Phase 4-5-6-7 |

## License

MIT
