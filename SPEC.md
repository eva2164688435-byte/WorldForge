# 世界观定制工具 - SPEC.md

## 1. Concept & Vision

一个沉浸式的世界观定制工具，帮助创作者构建完整的故事世界。界面设计灵感来源于古老的神秘学文献与现代极简主义的融合，营造出一种"创作即仪式"的氛围。整体感觉应该是庄重而富有魔力的，让用户在创建角色、城市和种族时感受到创造的喜悦。

## 2. Design Language

### 美学方向
神秘古典主义 + 现代卡片式UI。深色主题配合金色点缀，模拟羊皮纸与墨水的质感。

### 色彩系统
- Primary: `#1a1a2e` (深邃夜空)
- Secondary: `#16213e` (午夜蓝)
- Accent: `#d4af37` (古金色)
- Background: `#0f0f1a` (墨黑)
- Surface: `#252542` (暗紫灰)
- Text Primary: `#e8e8e8` (象牙白)
- Text Secondary: `#8b8b9e` (灰紫)
- Success: `#4ade80`
- Error: `#f87171`

### 字体
- 标题: "Cinzel", serif (古典衬线)
- 正文: "Noto Sans SC", sans-serif (中文优化)
- 装饰: "MedievalSharp", cursive (可选装饰元素)

### 空间系统
- 基础单位: 8px
- 卡片圆角: 12px
- 组件间距: 16px / 24px / 32px
- 页面边距: 32px (桌面) / 16px (移动)

### 动效哲学
- 页面切换: 淡入淡出 300ms ease-out
- 卡片悬停: 微微上浮 + 金色边框发光
- 按钮点击: 轻微缩放 0.98 + 涟漪效果
- 数据保存: 脉冲式确认动画
- 滚动: 平滑滚动

### 视觉资源
- 图标: Lucide Icons (线条风格)
- 装饰: CSS实现的分隔线与角标
- 背景: 细微的噪点纹理 + 渐变光晕

## 3. Layout & Structure

### 整体架构
单页应用，左侧导航 + 右侧内容区

```
┌─────────────────────────────────────────────────┐
│  Logo          世界观定制工具           [保存]  │
├────────┬────────────────────────────────────────┤
│        │                                        │
│  导航   │         主内容区                       │
│        │                                        │
│ 人物卡  │   根据选择显示对应的创建/浏览界面       │
│ 城镇    │                                        │
│ 种族    │                                        │
│        │                                        │
└────────┴────────────────────────────────────────┘
```

### 响应式策略
- 桌面 (>1024px): 侧边导航 + 宽内容区
- 平板 (768-1024px): 可折叠侧边栏
- 手机 (<768px): 底部导航 + 全屏内容

## 4. Features & Interactions

### 4.1 人物卡制造
**字段:**
- 姓名 (必填)
- 称号/别名
- 性别
- 年龄
- 种族 (关联已创建的种族)
- 职业/身份
- 外貌描述 (多行文本)
- 性格特点 (标签输入)
- 背景故事 (富文本)
- 特殊能力/技能 (列表)
- 人物关系 (关联其他人物)
- 头像 (URL输入或emoji选择)

**交互:**
- 实时预览卡片效果
- 拖拽排序人物关系
- 自动保存到localStorage
- 导出为JSON或打印友好格式

### 4.2 城镇设定制造
**字段:**
- 城镇名称 (必填)
- 所在地类型 (平原/山脉/海岸/森林/沙漠/其他)
- 人口规模
- 气候特征
- 建筑风格
- 特色产业
- 统治结构
- 重要地标 (列表)
- 著名人物 (关联人物)
- 历史背景
- 传闻/秘密

**交互:**
- 地图占位区域 (可放图片)
- 列表展示所有城镇

### 4.3 种族制造
**字段:**
- 种族名称 (必填)
- 别称
- 起源地
- 外貌特征
- 生理特征 (寿命/体型/特殊感官)
- 文化与习俗
- 语言/文字
- 与其他种族的关系
- 特殊能力
- 知名人物 (关联人物)

**交互:**
- 种族关系可视化图示
- 创建后可被人物引用

### 4.4 数据管理
- localStorage持久化
- 导出全部数据为JSON
- 导入JSON数据
- 清空确认对话框

## 5. Component Inventory

### 5.1 导航项 (NavItem)
- Default: 文字 + 图标，透明度0.7
- Hover: 透明度1 + 左侧金色指示条
- Active: 金色背景高亮 + 文字加粗

### 5.2 卡片组件 (ContentCard)
- Default: 深色背景，圆角，微妙边框
- Hover: 上浮4px，金色边框发光
- 内含标题、内容、操作按钮

### 5.3 表单输入 (FormInput)
- Default: 深色背景，底部边框
- Focus: 金色底部边框 + 轻微发光
- Error: 红色边框 + 错误提示文字

### 5.4 标签输入 (TagInput)
- 显示已添加标签为可删除小方块
- 输入框获取焦点时显示金色边框
- Enter键添加新标签

### 5.5 按钮 (Button)
- Primary: 金色背景，深色文字
- Secondary: 透明背景，金色边框
- Hover: 亮度提升
- Active: 轻微缩放
- Disabled: 透明度0.5

### 5.6 数据卡片展示 (DataCard)
- 网格布局展示已创建的项目
- 悬停显示编辑/删除按钮
- 点击进入编辑模式

### 5.7 空状态 (EmptyState)
- 居中显示图标 + 提示文字
- 提供快速创建入口

### 5.8 确认对话框 (ConfirmDialog)
- 模态遮罩
- 标题 + 描述 + 取消/确认按钮

## 6. Technical Approach

### 技术栈
- 纯HTML5 + CSS3 + Vanilla JavaScript
- 无框架依赖，单文件部署
- localStorage API 持久化

### 数据模型
```javascript
{
  characters: [
    {
      id: "uuid",
      name: "",
      title: "",
      gender: "",
      age: "",
      race: "",
      occupation: "",
      appearance: "",
      personality: [],
      backstory: "",
      abilities: [],
      relationships: [{id, type, characterId}],
      avatar: ""
    }
  ],
  towns: [
    {
      id: "uuid",
      name: "",
      terrain: "",
      population: "",
      climate: "",
      architecture: "",
      industry: "",
      governance: "",
      landmarks: [],
      notablePeople: [],
      history: "",
      rumors: ""
    }
  ],
  races: [
    {
      id: "uuid",
      name: "",
      aliases: "",
      origin: "",
      appearance: "",
      physiology: "",
      culture: "",
      language: "",
      relations: [],
      abilities: [],
      notableMembers: []
    }
  ]
}
```

### 关键实现
- 使用crypto.randomUUID()生成ID
- CSS Grid/Flexbox布局
- CSS变量管理主题色
- 事件委托处理动态元素
- 防抖保存避免频繁写入
