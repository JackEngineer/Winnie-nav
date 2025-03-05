# 维尼导航-手机端

<p align="center">
  <img src="./public/logo.png" alt="维尼导航" width="120">
</p>

<p align="center">
  <a href="#项目简介">项目简介</a> •
  <a href="#技术路线">技术路线</a> •
  <a href="#快速启动">快速启动</a> •
  <a href="#功能特点">功能特点</a> •
  <a href="#项目结构">项目结构</a> •
  <a href="#开发指南">开发指南</a>
</p>

## 🌐 项目简介

这是一个导航网站的手机端页面，提供快速访问常用资源的入口。支持个性化书签展示。用户可以自定义添加、编辑和删除书签，按照分类整理，实现高效的网络资源管理。

### 项目背景

随着移动互联网的普及，人们越来越多地使用手机进行网络浏览。然而，在移动端管理和访问常用网站仍然不够便捷。维尼导航就是为解决这一问题而生，它提供了一种简单、高效的方式来组织和访问用户的常用网站，让移动端的网络导航变得更加顺畅。

### 项目目标

- 提供简洁、美观的移动端导航界面
- 支持用户自定义书签和分类管理
- 实现快速搜索和访问功能
- 通过PWA技术提升用户体验
- 保证数据安全和隐私保护

## 🛠 技术路线

- **核心框架** : Vue3 + TypeScript
- **UI组件库** : [Vant 4.x](https://vant-ui.github.io/vant/#/zh-CN) （专为移动端设计的Vue组件库）
- **样式方案** : [Tailwind CSS]( https://www.tailwindcss.cn/ ) （原子化CSS框架）
- **状态管理** : Pinia
- **构建工具** : Vite
- **PWA支持** : Workbox

### 技术选型理由

- **Vue3 + TypeScript**: 提供类型安全和更好的开发体验，Composition API使代码更加模块化和可重用
- **Vant**: 专为移动端开发的UI库，提供丰富的移动端组件，减少开发工作量
- **Tailwind CSS**: 原子化CSS框架，加快UI开发速度，减少CSS维护成本
- **Pinia**: Vue官方推荐的状态管理方案，对TypeScript支持更好，API更简洁
- **Vite**: 基于ESM的构建工具，提供极速的开发服务器和优化的构建过程
- **Workbox**: 简化PWA开发流程，提供可靠的Service Worker方案

## 🚀 快速启动

### 环境要求

- Node.js >= 18.0.0
- npm >= 10.0.0 或 yarn >= 4.0.0 或 pnpm >= 9.0.0
- 现代浏览器（支持ES6+）

### 安装依赖

```bash
# 使用npm
npm install

# 或使用yarn
yarn install

# 或使用pnpm
pnpm install
```

### 开发模式

```bash
# 使用npm
npm run dev

# 或使用yarn
yarn dev

# 或使用pnpm
pnpm dev
```

开发服务器将在 <http://localhost:5173> 启动（或下一个可用端口）

### 构建生产版本

```bash
# 使用npm
npm run build

# 或使用yarn
yarn build

# 或使用pnpm
pnpm build
```

### 构建后预览

```bash
# 使用npm
npm run preview

# 或使用yarn
yarn preview

# 或使用pnpm
pnpm preview
```

### 环境变量配置

项目使用`.env`文件管理环境变量。可以创建以下文件来覆盖默认配置：

- `.env` - 所有环境
- `.env.development` - 开发环境
- `.env.production` - 生产环境

示例：

```
# .env.development
VITE_API_BASE_URL=http://localhost:3000/api
VITE_ENABLE_MOCK=true
```

## 📂 项目结构

```text
winnie-nav-mobile/
├── public/                 # 静态资源目录
│   ├── favicon.ico         # 网站图标
│   ├── manifest.json       # PWA配置文件
│   └── icons/              # PWA图标
├── src/                    # 源代码目录
│   ├── assets/             # 资源文件(图片、字体等)
│   ├── components/         # 公共组件
│   │   ├── common/         # 通用组件
│   │   ├── layout/         # 布局组件
│   │   └── business/       # 业务组件
│   ├── views/              # 页面视图
│   │   ├── home/           # 首页
│   │   ├── search/         # 搜索页
│   │   ├── settings/       # 设置页
│   │   └── bookmark/       # 书签管理页
│   ├── router/             # 路由配置
│   │   ├── index.ts        # 路由入口
│   │   └── routes.ts       # 路由定义
│   ├── stores/             # Pinia状态管理
│   │   ├── bookmark.ts     # 书签状态
│   │   ├── category.ts     # 分类状态
│   │   └── user.ts         # 用户状态
│   ├── services/           # API服务和数据处理
│   │   ├── api.ts          # API接口定义
│   │   └── storage.ts      # 本地存储服务
│   ├── utils/              # 工具函数
│   │   ├── http.ts         # HTTP请求封装
│   │   └── validators.ts   # 数据验证工具
│   ├── styles/             # 全局样式
│   │   ├── index.css       # 主样式文件
│   │   └── variables.css   # CSS变量
│   ├── types/              # TypeScript类型定义
│   │   ├── bookmark.ts     # 书签相关类型
│   │   └── common.ts       # 通用类型
│   ├── App.vue             # 根组件
│   ├── main.ts             # 入口文件
│   └── env.d.ts            # 环境变量类型声明
├── .eslintrc.js            # ESLint配置
├── .prettierrc             # Prettier配置
├── tailwind.config.js      # Tailwind配置
├── tsconfig.json           # TypeScript配置
├── vite.config.ts          # Vite配置
├── index.html              # HTML模板
├── package.json            # 项目依赖配置
├── README.md               # 项目说明文档
└── LICENSE                 # 许可证文件
```

## ✨ 功能特点

### 📱 移动端优先

- 专为手机端设计的UI界面
- 响应式布局，适配各种屏幕尺寸
- 触摸友好的交互体验
- 支持手势操作（滑动切换、下拉刷新等）

### 🔖 书签管理

- 分类展示常用网站书签
- 支持添加、编辑、删除书签
- 拖拽排序，个性化展示
- 批量操作（移动、删除等）
- 收藏夹功能

### 🔍 搜索功能

- 快速搜索已添加的书签
- 支持模糊匹配和精确搜索
- 搜索历史记录
- 智能推荐功能
- 支持语音搜索（规划中）

### 🌓 主题切换

- 支持亮色/暗色主题
- 跟随系统主题自动切换
- 自定义主题色彩
- 多种预设主题可选

### 📲 PWA支持

- 支持添加到主屏幕
- 离线访问能力
- 快速启动和响应
- 后台同步数据
- 推送通知（规划中）

### 🔄 数据同步

- 本地存储书签数据
- 支持导入/导出数据
- 云端同步功能（规划中）

## 🧩 组件设计

项目使用模块化的组件设计，主要包括：

### 核心组件

- **NavBar**: 顶部导航栏组件
  - 提供页面标题、返回按钮和操作菜单
  - 支持自定义右侧按钮和插槽

- **TabBar**: 底部标签栏组件
  - 提供主要导航功能
  - 支持徽标和自定义图标

- **BookmarkCard**: 书签卡片组件
  - 展示单个书签信息
  - 支持长按操作菜单
  - 提供编辑和删除功能

- **CategoryList**: 分类列表组件
  - 展示书签分类
  - 支持展开/折叠功能
  - 分类管理接口

- **SearchBar**: 搜索栏组件
  - 提供搜索输入和建议
  - 历史记录展示
  - 语音输入接口

- **SettingPanel**: 设置面板组件
  - 主题设置
  - 数据管理
  - 用户首选项

### 组件示例

```vue
<!-- BookmarkCard.vue 示例 -->
<template>
  <div 
    class="bookmark-card rounded-lg p-3 flex items-center shadow-sm"
    @click="handleClick"
    @long-press="handleLongPress"
  >
    <div class="bookmark-icon mr-3">
      <img v-if="bookmark.icon" :src="bookmark.icon" :alt="bookmark.title" class="w-10 h-10 rounded">
      <div v-else class="w-10 h-10 rounded bg-primary flex items-center justify-center text-white">
        {{ bookmark.title.charAt(0) }}
      </div>
    </div>
    <div class="flex-1 overflow-hidden">
      <h3 class="text-base font-medium truncate">{{ bookmark.title }}</h3>
      <p class="text-sm text-gray-500 truncate">{{ bookmark.url }}</p>
    </div>
    <div class="bookmark-actions">
      <van-icon name="ellipsis" @click.stop="showActions" />
    </div>
  </div>
</template>
```

## 🛠️ 开发指南

### 新建项目

如果你想从头开始一个新项目，可以使用以下命令：

```bash
# 使用 npm
npm create vite@latest winnie-nav-mobile -- --template vue-ts

# 或使用 yarn
yarn create vite winnie-nav-mobile --template vue-ts

# 或使用 pnpm
pnpm create vite winnie-nav-mobile --template vue-ts
```

### 安装核心依赖

```bash
# 安装Vant
npm add vant

# 安装Tailwind CSS
npm add -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

# 安装Pinia
npm add pinia

# 安装Vue Router
npm add vue-router

# 安装PWA支持
npm add -D vite-plugin-pwa
```

### 添加新组件

1. 在 `src/components` 目录下创建新的组件文件
2. 使用 Vue3 的 `<script setup>` 语法编写组件
3. 在需要的地方导入并使用该组件

示例：

```vue
<!-- src/components/common/IconButton.vue -->
<script setup lang="ts">
defineProps<{
  icon: string;
  text?: string;
  disabled?: boolean;
}>();

const emit = defineEmits<{
  (e: 'click', event: MouseEvent): void;
}>();

const handleClick = (event: MouseEvent) => {
  emit('click', event);
};
</script>

<template>
  <button 
    class="icon-button flex flex-col items-center justify-center p-2 rounded-lg"
    :class="{ 'opacity-50': disabled }"
    :disabled="disabled"
    @click="handleClick"
  >
    <van-icon :name="icon" class="text-xl mb-1" />
    <span v-if="text" class="text-xs">{{ text }}</span>
  </button>
</template>
```

使用组件：

```vue
<template>
  <div>
    <IconButton icon="plus" text="添加" @click="addBookmark" />
  </div>
</template>

<script setup lang="ts">
import IconButton from '@/components/common/IconButton.vue';

const addBookmark = () => {
  // 处理添加书签的逻辑
};
</script>
```

### 状态管理

项目使用 Pinia 进行状态管理，主要 store 包括：

- `bookmarkStore`: 管理书签数据
- `categoryStore`: 管理分类数据
- `userStore`: 管理用户设置

示例 Store：

```typescript
// src/stores/bookmark.ts
import { defineStore } from 'pinia';
import { ref, computed } from 'vue';
import type { Bookmark } from '@/types/bookmark';
import { StorageService } from '@/services/storage';

export const useBookmarkStore = defineStore('bookmark', () => {
  const bookmarks = ref<Bookmark[]>([]);
  const loading = ref(false);
  const error = ref<string | null>(null);

  // 获取书签列表
  const fetchBookmarks = async () => {
    loading.value = true;
    error.value = null;
    try {
      const data = await StorageService.getItem('bookmarks');
      bookmarks.value = data || [];
    } catch (err) {
      error.value = '获取书签失败';
      console.error(err);
    } finally {
      loading.value = false;
    }
  };

  // 添加书签
  const addBookmark = async (bookmark: Omit<Bookmark, 'id'>) => {
    const newBookmark: Bookmark = {
      ...bookmark,
      id: Date.now().toString(),
      createdAt: Date.now(),
      updatedAt: Date.now(),
    };
    
    bookmarks.value.push(newBookmark);
    await saveBookmarks();
    return newBookmark;
  };

  // 根据分类获取书签
  const getBookmarksByCategory = computed(() => (categoryId: string) => {
    return bookmarks.value.filter(bookmark => bookmark.categoryId === categoryId);
  });

  // 保存书签到本地存储
  const saveBookmarks = async () => {
    await StorageService.setItem('bookmarks', bookmarks.value);
  };

  return {
    bookmarks,
    loading,
    error,
    fetchBookmarks,
    addBookmark,
    getBookmarksByCategory,
  };
});
```

使用 Store：

```vue
<script setup lang="ts">
import { useBookmarkStore } from '@/stores/bookmark';
import { onMounted } from 'vue';

const bookmarkStore = useBookmarkStore();

onMounted(() => {
  bookmarkStore.fetchBookmarks();
});

const addNewBookmark = async () => {
  await bookmarkStore.addBookmark({
    title: '新书签',
    url: 'https://example.com',
    categoryId: 'default',
  });
};
</script>

<template>
  <div>
    <div v-if="bookmarkStore.loading">加载中...</div>
    <div v-else-if="bookmarkStore.error">{{ bookmarkStore.error }}</div>
    <div v-else>
      <div v-for="bookmark in bookmarkStore.bookmarks" :key="bookmark.id">
        {{ bookmark.title }}
      </div>
      <button @click="addNewBookmark">添加书签</button>
    </div>
  </div>
</template>
```

### 数据结构设计

项目的核心数据结构如下：

```typescript
// src/types/bookmark.ts

// 书签数据结构
export interface Bookmark {
  id: string;           // 唯一标识符
  title: string;        // 书签标题
  url: string;          // 书签URL
  icon?: string;        // 图标URL（可选）
  description?: string; // 描述（可选）
  categoryId: string;   // 所属分类ID
  tags?: string[];      // 标签（可选）
  order: number;        // 排序位置
  createdAt: number;    // 创建时间戳
  updatedAt: number;    // 更新时间戳
}

// 分类数据结构
export interface Category {
  id: string;           // 唯一标识符
  name: string;         // 分类名称
  icon?: string;        // 图标（可选）
  color?: string;       // 颜色（可选）
  order: number;        // 排序位置
  createdAt: number;    // 创建时间戳
  updatedAt: number;    // 更新时间戳
  parentId?: string;    // 父分类ID（可选，用于子分类）
}

// 用户设置
export interface UserSettings {
  theme: 'light' | 'dark' | 'system'; // 主题设置
  accentColor: string;                // 强调色
  layout: 'grid' | 'list';            // 布局方式
  iconSize: 'small' | 'medium' | 'large'; // 图标大小
  openMethod: 'same-tab' | 'new-tab'; // 打开方式
  autoSync: boolean;                  // 自动同步
}
```

### 样式开发

1. 优先使用 Tailwind CSS 的原子类
2. 对于复杂样式，可在组件内使用 `<style>` 块
3. 全局样式定义在 `src/styles` 目录下

Tailwind CSS 配置示例：

```javascript
// tailwind.config.js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{vue,js,ts,jsx,tsx}",
  ],
  darkMode: 'class', // 或 'media'
  theme: {
    extend: {
      colors: {
        primary: {
          DEFAULT: '#3A86FF',
          dark: '#2563EB',
          light: '#60A5FA',
        },
        secondary: {
          DEFAULT: '#FB5607',
          dark: '#D04300',
          light: '#FF7A43',
        },
      },
      fontFamily: {
        sans: ['PingFang SC', 'Helvetica Neue', 'Arial', 'sans-serif'],
      },
    },
  },
  plugins: [],
}
```

### 调试技巧

1. **Vue DevTools**：使用Vue DevTools浏览器扩展进行组件和状态调试
   - 安装：[Chrome扩展](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)

2. **移动设备预览**：
   - 使用Chrome DevTools的设备模拟器
   - 或通过局域网IP访问，在真实移动设备上预览

3. **调试日志**：

   ```typescript
   // 创建调试工具
   // src/utils/debug.ts
   const DEBUG = import.meta.env.DEV;
   
   export const debug = {
     log: (...args: any[]) => {
       if (DEBUG) console.log('[Debug]', ...args);
     },
     error: (...args: any[]) => {
       if (DEBUG) console.error('[Error]', ...args);
     },
     warn: (...args: any[]) => {
       if (DEBUG) console.warn('[Warn]', ...args);
     },
   };
   ```

4. **性能监控**：

   ```typescript
   // 性能计时
   const start = performance.now();
   // 执行操作
   const end = performance.now();
   debug.log(`Operation took ${end - start}ms`);
   ```

### 性能优化建议

1. **组件懒加载**：

   ```typescript
   // router/index.ts
   const Home = () => import('../views/home/index.vue');
   const Search = () => import('../views/search/index.vue');
   ```

2. **列表虚拟化**：对于长列表，使用虚拟滚动技术

   ```bash
   npm add vue-virtual-scroller
   ```

3. **图片优化**：
   - 使用适当尺寸的图片
   - 懒加载图片
   - 使用WebP格式

4. **代码分割**：使用动态导入拆分代码包

5. **Service Worker缓存**：合理配置PWA缓存策略

## 📝 贡献指南

1. Fork 本仓库
2. 创建你的特性分支 (`git checkout -b feature/amazing-feature`)
3. 提交你的更改 (`git commit -m 'Add some amazing feature'`)
4. 推送到分支 (`git push origin feature/amazing-feature`)
5. 开启一个 Pull Request

### 代码规范

- 遵循 [Vue 风格指南](https://cn.vuejs.org/style-guide/)
- 使用 ESLint 和 Prettier 保持代码风格一致
- 组件名使用多词合成（如：BookmarkList 而不是 Bookmarks）
- 提交信息遵循 [Conventional Commits](https://www.conventionalcommits.org/zh-hans/) 规范

### 测试

在提交代码前，请确保：

1. 运行并通过所有测试

   ```bash
   npm run test
   ```

2. 检查代码风格

   ```bash
   npm run lint
   ```

## ❓ 常见问题解答

### Q: 如何添加新的书签分类？

A: 在设置页面中，点击"分类管理"，然后点击"添加分类"按钮。填写分类名称和选择图标后保存即可。

### Q: 数据存储在哪里？

A: 当前版本将数据存储在浏览器的本地存储中。未来版本计划添加云端同步功能。

### Q: 如何导出我的书签数据？

A: 在设置页面中，点击"数据管理"，然后点击"导出数据"按钮，将生成一个JSON文件供你下载。

### Q: 如何更改主题颜色？

A: 在设置页面中，点击"主题设置"，选择预设主题或自定义颜色方案。

## 📄 许可证

本项目基于 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

## 📊 版本历史

- **v0.1.0** - 初始版本
  - 基本书签管理功能
  - 分类展示
  - 本地存储数据

## 📞 联系方式

- 项目维护者: [维护者姓名](mailto:email@example.com)
- 项目主页: [GitHub仓库链接](https://github.com/yourusername/winnie-nav-mobile)

---

<p align="center">Made with ❤️ for better mobile browsing</p>
