# diygod.cc 首页 / 文章 / 项目页复刻分析

## 目标
基于对 `https://diygod.cc/` 的页面结构观察，整理一份适合前端实现的线框与组件说明，用于复刻：

- 首页
- 文章列表页
- 项目列表页

目标是实现 **结构一致、视觉气质接近、交互相似** 的内容型个人站点，而不是逐像素复制。

---

## 一、整体风格总结

### 视觉气质
- 个人博客 / 独立开发者主页风格
- 内容优先，装饰克制
- 有作者个人品牌感
- 支持浅色 / 深色主题
- 支持中文 / 英文切换

### 设计关键词
- 简洁
- 温和
- 留白充足
- 卡片化
- 图片驱动
- 阅读友好

### 全站共性
- 顶部导航固定一致
- 页面结构清晰，层级简单
- 首页突出作者身份与精选内容
- 文章页偏纵向阅读流
- 项目页偏卡片宫格浏览

---

## 二、全站信息架构

```text
Site
├─ Header
│  ├─ Brand
│  ├─ MainNav
│  ├─ LocaleSwitch
│  └─ ThemeToggle
├─ Main Content
│  ├─ Home
│  ├─ Posts
│  └─ Projects
├─ Footer
│  ├─ SiteInfo
│  ├─ Runtime
│  └─ Sitemap
└─ LocalePrompt
```

### 主导航建议
- 首页
- 文章
- 项目
- 友邻
- 关于

### 全局交互建议
- 主题切换：浅色 / 深色
- 语言切换：中文 / English
- 卡片 hover 高亮
- 所有内容卡片整块可点击

---

## 三、首页复刻结构

## 1. 页面目标
首页承担三件事：

1. 介绍作者
2. 展示精选文章
3. 展示代表项目

## 2. 线框结构

```text
HomePage
├─ Header
├─ HeroSection
│  ├─ Greeting
│  ├─ Intro
│  ├─ Description
│  ├─ SocialLinks
│  └─ Avatar
├─ FeaturedPostsSection
│  ├─ SectionTitle
│  ├─ CategoryOrTagEntry
│  ├─ PostPreviewList
│  └─ ViewAllPosts
├─ FeaturedProjectsSection
│  ├─ SectionTitle
│  ├─ ProjectPreviewGrid
│  └─ ViewAllProjects
├─ Footer
└─ LocalePrompt
```

## 3. Hero 区建议内容

### 左侧内容
- 大标题：一句欢迎语 / 身份标识
- 副标题：一句简短自我介绍
- 长描述：个人定位、兴趣、创作方向
- 社交链接：RSS、GitHub、X、Telegram、B 站、邮箱、豆瓣等

### 右侧内容
- 头像或人物插图

## 4. Hero 布局建议

### 桌面端
- 左文右图双栏布局
- 左侧宽，右侧作为视觉锚点

### 移动端
- 改为单栏堆叠
- 文案在上，头像在下

## 5. 首页文章区
- 展示 3~6 篇精选文章
- 每篇文章展示：
  - 标题
  - 摘要
  - 日期
  - 分类
  - 标签
  - 封面图
- 底部提供“查看所有文章”按钮

## 6. 首页项目区
- 展示 4~8 个代表项目
- 每个项目展示：
  - Logo / 缩略图
  - 项目名
  - 一句话描述
  - 跳转链接
- 底部提供“查看所有项目”按钮

---

## 四、文章列表页复刻结构

## 1. 页面目标
文章页是典型内容归档页，重点是：

- 浏览文章
- 搜索文章
- 按分类 / 标签进入归档

## 2. 线框结构

```text
PostsPage
├─ Header
├─ PostsHero
│  ├─ PageTitle
│  ├─ SearchInput
│  └─ ResultCount
├─ PostList
│  └─ PostCard[]
│     ├─ Title
│     ├─ Excerpt
│     ├─ MetaRow
│     │  ├─ Date
│     │  ├─ CategoryLink
│     │  └─ TagLinks
│     └─ CoverImage
├─ EmptyState
├─ Footer
└─ LocalePrompt
```

## 3. 文章卡片结构

```text
PostCard
├─ TitleLink
├─ Excerpt
├─ MetaRow
│  ├─ Date
│  ├─ Category
│  └─ Tags
└─ CoverImage
```

## 4. 文章卡片特点
- 标题是最强视觉重点
- 摘要 1~3 行，避免过长
- 元信息弱化显示
- 封面图放在卡片下方或右侧
- 有图和无图都应兼容

## 5. 搜索与筛选建议

### 搜索
- 页面顶部放搜索框
- 输入关键词即时过滤
- 显示文章总数 / 当前结果数
- 无结果时显示空状态

### 分类 / 标签
- 分类可点击进入分类归档页
- 标签可点击进入标签归档页
- 不需要复杂多选筛选器

## 6. 布局建议

### 桌面端
- 单栏纵向列表
- 宽内容区，适合阅读

### 移动端
- 维持单栏
- 缩小封面图高度
- 控制摘要长度

---

## 五、项目列表页复刻结构

## 1. 页面目标
项目页核心是快速浏览作者作品，并跳转到项目详情或外部地址。

## 2. 线框结构

```text
ProjectsPage
├─ Header
├─ PageTitle
├─ ProjectGrid
│  └─ ProjectCard[]
│     ├─ Image
│     ├─ Title
│     └─ Description
├─ Footer
└─ LocalePrompt
```

## 3. 项目卡片结构

```text
ProjectCard
├─ CoverImage
├─ ProjectTitle
└─ ProjectDescription
```

## 4. 项目卡片特点
- 图片承担主要吸引力
- 名称负责识别
- 描述只做一句补充
- 整张卡片可点击

## 5. 布局建议

### 桌面端
- 使用响应式网格
- 2~4 列随容器宽度变化

### 移动端
- 1 列或 2 列
- 保证点击区域足够大

### 推荐 Grid 写法
```css
.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 24px;
}
```

---

## 六、推荐组件拆分

```text
components/
├─ layout/
│  ├─ SiteHeader
│  ├─ MainNav
│  ├─ ThemeToggle
│  ├─ LocaleSwitch
│  └─ SiteFooter
├─ common/
│  ├─ SectionTitle
│  ├─ SocialLinks
│  ├─ EmptyState
│  └─ LocalePrompt
├─ home/
│  ├─ HeroSection
│  ├─ FeaturedPosts
│  └─ FeaturedProjects
├─ post/
│  ├─ PostCard
│  ├─ PostMeta
│  ├─ PostSearch
│  └─ TagList
└─ project/
   ├─ ProjectGrid
   └─ ProjectCard
```

---

## 七、数据结构建议

### Post
```ts
type Post = {
  title: string
  slug: string
  excerpt: string
  date: string
  category: string
  tags: string[]
  cover?: string
}
```

### Project
```ts
type Project = {
  title: string
  description: string
  image: string
  href: string
}
```

### SocialLink
```ts
type SocialLink = {
  label: string
  href: string
  icon: string
}
```

---

## 八、样式复刻重点

如果要尽量接近原站气质，优先关注这些点：

### 1. 字体
- 中文正文要清晰耐读
- 标题需要明显的层级差
- 中英混排不能突兀

### 2. 留白
- 页面边距不能太小
- 区块之间要有明显呼吸感
- 卡片内部上下间距要均匀

### 3. 配色
- 用中性色背景作为基础
- 用少量强调色点缀交互元素
- 浅色 / 深色两套主题都要完整定义

### 4. 卡片风格
- 圆角适中
- 边框或浅阴影保持克制
- hover 时有轻微浮起或背景变化

### 5. 图片
- 文章封面与项目图应统一比例
- 加载失败时要有占位方案

---

## 九、实现建议

### 技术栈推荐
优先推荐：
- Astro
- Next.js
- Nuxt 3

如果你当前项目已经是 Astro，这类内容型站点非常适合继续用 Astro 实现。

### 推荐实现顺序
1. 先搭全站 Layout
2. 实现 Header / Footer / 主题切换 / 语言切换
3. 实现首页 Hero
4. 实现文章卡片与文章列表页
5. 实现项目卡片与项目页
6. 最后统一细调间距、配色、hover、响应式

---

## 十、复刻可行性结论

### 可复刻部分
- 首页结构
- 文章列表页结构
- 项目页结构
- 内容卡片样式
- 明暗主题
- 中英文切换

### 需要进一步观察才能高度还原的部分
- 精确字体
- 实际间距值
- 动画时长与 easing
- hover 细节
- 响应式断点策略
- 图片裁切比例

### 最终结论
这个站点的首页、文章页、项目页都属于 **很适合前端复刻的内容型页面**。

如果目标是：
- **结构一致**：完全可做
- **风格相近**：完全可做
- **高相似视觉还原**：需要进一步对真实页面样式做细节采样
