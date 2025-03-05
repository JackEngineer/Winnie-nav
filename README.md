# 维尼导航

<p align="center">
  <img src="./frontend/public/logo.png" alt="维尼导航" width="120">
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

这是一个导航网站的手机端页面，提供快速访问常用资源的入口。支持个性化书签展示。用户可以自定义添加、编辑和删除书签，按照分类整理，实现高效的网络资源管理。项目采用前后端分离架构，前端使用Vue3开发，后端使用Django REST Framework提供API服务。

### 项目背景

随着移动互联网的普及，人们越来越多地使用手机进行网络浏览。然而，在移动端管理和访问常用网站仍然不够便捷。维尼导航就是为解决这一问题而生，它提供了一种简单、高效的方式来组织和访问用户的常用网站，让移动端的网络导航变得更加顺畅。

### 项目目标

- 提供简洁、美观的移动端导航界面
- 支持用户自定义书签和分类管理
- 实现快速搜索和访问功能
- 通过PWA技术提升用户体验
- 保证数据安全和隐私保护
- 支持云端数据同步与备份
- 实现多设备数据共享

### 性能指标

项目定义了以下关键性能指标作为开发和优化目标：

1. **前端性能**
   - 首次内容绘制(FCP) < 1.5秒
   - 交互时间(TTI) < 3秒
   - 首次输入延迟(FID) < 100ms
   - 累积布局偏移(CLS) < 0.1
   - 离线启动时间 < 2秒

2. **API性能**
   - 95%的API请求响应时间 < 300ms
   - 99%的API请求响应时间 < 1秒
   - API错误率 < 0.1%
   - REST接口稳定性 > 99.9%

3. **数据同步性能**
   - 在线数据同步延迟 < 2秒
   - 冲突发生率 < 0.01%
   - 冲突解决时间 < 5秒（自动解决）
   - 大量数据导入性能 > 100条/秒

4. **系统扩展性**
   - 单服务器支持并发用户 > 5000
   - 单用户书签容量 > 10000条
   - 系统容量线性扩展（添加资源）
   - 峰值负载下响应时间增加 < 50%

## 🏗️ 系统架构

### 整体架构图

<p align="center">
  <img src="./docs/images/architecture-diagram.png" alt="维尼导航架构图" width="700">
</p>

维尼导航采用经典的前后端分离架构，同时整合了PWA能力以增强移动端体验：

- **前端层**：Vue3应用以PWA方式部署，支持离线访问和本地数据缓存
- **API网关层**：处理认证、限流、请求路由
- **应用服务层**：Django REST Framework实现核心业务逻辑
- **数据持久层**：PostgreSQL存储结构化数据，Redis提供缓存和会话存储

### 数据流图

<p align="center">
  <img src="./docs/images/data-flow-diagram.png" alt="数据流图" width="700">
</p>

系统中的数据流动遵循以下路径：

1. 用户在前端添加/修改书签
2. 数据通过REST API发送到后端服务
3. 数据经过验证和处理后存入数据库
4. 同时更新Redis缓存
5. 变更通过WebSocket推送给客户端
6. 前端更新本地存储以支持离线访问

### 部署架构

<p align="center">
  <img src="./docs/images/deployment-diagram.png" alt="部署架构图" width="700">
</p>

项目支持多种部署模式：

- **开发环境**：前后端分离部署，独立开发服务器
- **测试环境**：Docker Compose集成部署，模拟生产环境
- **生产环境**：Nginx + Gunicorn + Django + PostgreSQL + Redis，采用容器化部署

## 🛠 技术路线

### 前端技术栈

- **核心框架** : Vue3 + TypeScript
- **UI组件库** : [Vant 4.x](https://vant-ui.github.io/vant/#/zh-CN) （专为移动端设计的Vue组件库）
- **样式方案** : [Tailwind CSS]( https://www.tailwindcss.cn/ ) （原子化CSS框架）
- **状态管理** : Pinia
- **构建工具** : Vite
- **PWA支持** : Workbox

### 后端技术栈

- **核心框架** : Django 4.x + Python 3.10+
- **API框架** : Django REST Framework
- **数据库** : PostgreSQL (生产环境) / SQLite (开发环境)
- **缓存** : Redis
- **认证** : JWT (JSON Web Token)
- **文档** : Swagger / ReDoc
- **任务队列** : Celery (异步任务处理)
- **测试** : pytest
- **容器化** : Docker & Docker Compose

### 技术选型理由

#### 前端技术选型

- **Vue3 + TypeScript**: 提供类型安全和更好的开发体验，Composition API使代码更加模块化和可重用
- **Vant**: 专为移动端开发的UI库，提供丰富的移动端组件，减少开发工作量
- **Tailwind CSS**: 原子化CSS框架，加快UI开发速度，减少CSS维护成本
- **Pinia**: Vue官方推荐的状态管理方案，对TypeScript支持更好，API更简洁
- **Vite**: 基于ESM的构建工具，提供极速的开发服务器和优化的构建过程
- **Workbox**: 简化PWA开发流程，提供可靠的Service Worker方案

#### 后端技术选型

- **Django**: 成熟稳定的Python Web框架，提供完整的MVC架构和强大的后台管理功能
- **DRF**: 专为Django设计的REST API框架，简化API开发流程
- **PostgreSQL**: 强大的关系型数据库，支持JSON字段，适合存储书签数据
- **Redis**: 高性能缓存解决方案，减轻数据库压力
- **JWT**: 无状态认证方案，适合前后端分离架构
- **Celery**: 处理数据同步、定时任务等异步操作
- **Docker**: 简化部署流程，确保开发和生产环境一致性

### 数据库扩展策略

随着用户和数据量增长，系统采用以下策略确保数据库性能和可扩展性：

1. **读写分离**
   - 主库处理写操作，多个从库处理读操作
   - 使用Django database router路由读写请求
   - 支持异步复制和半同步复制模式

2. **分库分表**
   - 按用户ID范围进行水平分表
   - 热点数据和冷数据分离存储
   - 使用代理层屏蔽分片复杂性

3. **混合存储**
   - 结构化数据（用户、权限）存储在PostgreSQL
   - 考虑将书签内容存储在MongoDB以优化查询性能
   - 搜索功能通过Elasticsearch实现

4. **数据库监控**
   - 使用Prometheus监控数据库指标
   - 设置慢查询日志和性能阈值告警
   - 定期执行EXPLAIN分析优化查询

## 🚀 快速启动

### 环境要求

- Node.js >= 18.0.0
- npm >= 10.0.0 或 yarn >= 4.0.0 或 pnpm >= 9.0.0
- Python >= 3.10
- Docker & Docker Compose (可选，用于容器化部署)
- 现代浏览器（支持ES6+）

### 基础配置

1. 克隆本仓库:

```bash
git clone https://github.com/JackEngineer/Winnie-nav.git
cd Winnie-nav
```

2. 创建环境变量配置:

```bash
# 前端配置 (.env.development in frontend/)
cp frontend/.env.example frontend/.env.development

# 后端配置 (.env in backend/)
cp backend/.env.example backend/.env
```

### 使用Docker Compose启动整个应用

这是推荐的开发方式，可以一键启动前后端和数据库:

```bash
# 启动所有服务
docker-compose up -d

# 执行数据库迁移
docker-compose exec backend python manage.py migrate

# 创建超级用户
docker-compose exec backend python manage.py createsuperuser
```

应用将在以下地址可访问:

- 前端: <http://localhost:5173>
- 后端API: <http://localhost:8000/api/>
- 后端管理界面: <http://localhost:8000/admin/>

### 分别启动前后端（传统方式）

如果你不想使用Docker，也可以分别启动前后端:

#### 启动前端

```bash
# 进入前端目录
cd frontend

# 安装依赖
npm install
# 或
yarn install
# 或
pnpm install

# 启动开发服务器
npm run dev
# 或
yarn dev
# 或
pnpm dev
```

前端开发服务器将在 <http://localhost:5173> 启动（或下一个可用端口）

#### 启动后端

```bash
# 进入后端目录
cd backend

# 创建虚拟环境
python -m venv venv
source venv/bin/activate  # Linux/Mac
# 或
# venv\Scripts\activate  # Windows

# 安装依赖
pip install -r requirements/development.txt

# 数据库迁移
python manage.py migrate

# 创建超级用户
python manage.py createsuperuser

# 启动开发服务器
python manage.py runserver
```

后端API将在 <http://localhost:8000> 启动

### 环境变量配置

#### 前端环境变量

前端项目使用`.env`文件管理环境变量。可以创建以下文件来覆盖默认配置：

- `.env` - 所有环境
- `.env.development` - 开发环境
- `.env.production` - 生产环境

示例：

```
# frontend/.env.development
VITE_API_BASE_URL=http://localhost:8000/api/v1
VITE_ENABLE_MOCK=false
```

#### 后端环境变量

后端使用`.env`文件管理环境变量:

```
# backend/.env
DEBUG=True
SECRET_KEY=your-secret-key
DATABASE_URL=postgres://user:password@localhost:5432/winnie_nav
ALLOWED_HOSTS=localhost,127.0.0.1
CORS_ALLOWED_ORIGINS=http://localhost:5173
```

## 📂 项目结构

项目采用前后端分离但在同一仓库管理的结构:

```text
winnie-nav/                     # 项目根目录
├── frontend/                   # 前端代码(Vue3)
│   ├── public/                 # 静态资源目录
│   ├── src/                    # 源代码目录
│   │   ├── assets/             # 资源文件(图片、字体等)
│   │   ├── components/         # 公共组件
│   │   ├── views/              # 页面视图
│   │   ├── router/             # 路由配置
│   │   ├── stores/             # Pinia状态管理
│   │   ├── services/           # API服务和数据处理
│   │   ├── utils/              # 工具函数
│   │   ├── styles/             # 全局样式
│   │   ├── types/              # TypeScript类型定义
│   │   ├── App.vue             # 根组件
│   │   └── main.ts             # 入口文件
│   ├── .eslintrc.js            # ESLint配置
│   ├── tailwind.config.js      # Tailwind配置
│   ├── tsconfig.json           # TypeScript配置
│   ├── vite.config.ts          # Vite配置
│   ├── index.html              # HTML模板
│   └── package.json            # 项目依赖配置
├── backend/                    # 后端代码(Django)
│   ├── config/                 # 项目配置
│   │   ├── settings/           # Django设置
│   │   ├── urls.py             # 主URL配置
│   │   └── wsgi.py             # WSGI配置
│   ├── apps/                   # 应用模块
│   │   ├── accounts/           # 用户账户相关
│   │   ├── bookmarks/          # 书签相关
│   │   └── categories/         # 分类相关
│   ├── core/                   # 核心功能
│   │   ├── utils/              # 通用工具
│   │   ├── middleware/         # 中间件
│   │   ├── permissions/        # 权限类
│   │   └── pagination/         # 分页类
│   ├── templates/              # Django模板(用于管理界面)
│   ├── static/                 # 静态文件(用于管理界面)
│   ├── tests/                  # 测试代码
│   ├── docker/                 # Docker相关文件
│   ├── requirements/           # 依赖管理
│   ├── manage.py               # Django管理脚本
│   └── celery.py               # Celery配置
├── docker-compose.yml          # Docker Compose配置
├── .gitignore                  # Git忽略文件
├── README.md                   # 项目文档
└── LICENSE                     # 许可证文件
```

## ✨ 功能特点

### 前端功能

#### 📱 移动端优先

- 专为手机端设计的UI界面
- 响应式布局，适配各种屏幕尺寸
- 触摸友好的交互体验
- 支持手势操作（滑动切换、下拉刷新等）

#### 🔖 书签管理

- 分类展示常用网站书签
- 支持添加、编辑、删除书签
- 拖拽排序，个性化展示
- 批量操作（移动、删除等）
- 收藏夹功能

#### 🔍 搜索功能

- 快速搜索已添加的书签
- 支持模糊匹配和精确搜索
- 搜索历史记录
- 智能推荐功能
- 支持语音搜索（规划中）

#### 🌓 主题切换

- 支持亮色/暗色主题
- 跟随系统主题自动切换
- 自定义主题色彩
- 多种预设主题可选

#### 📲 PWA支持

- 支持添加到主屏幕
- 离线访问能力
- 快速启动和响应
- 后台同步数据
- 推送通知（规划中）

### 后端功能

#### 🔐 用户认证与授权

- JWT认证机制
- 用户注册、登录、密码重置
- 社交媒体OAuth登录（Google, GitHub等）
- 基于角色的权限控制
- 多设备同时登录支持

#### 📊 数据同步

- 实时数据同步
  - 基于WebSocket实现实时数据推送
  - 采用JWT携带认证信息确保连接安全
  - 支持断线重连和消息重传机制
- 冲突检测与解决
  - 使用乐观锁和版本号机制(ETag)处理并发编辑
  - 基于时间戳和优先级策略进行冲突解决
  - 提供冲突可视化界面辅助用户选择
- 数据版本控制
  - 保留书签和分类的历史版本
  - 支持历史版本浏览和回滚操作
  - 增量同步算法
  - 只传输变更数据，减少网络流量
  - 使用差异算法计算最小更新集
  - 支持批量同步和选择性同步

#### 🔍 智能推荐

- 基于用户行为的书签推荐
- 热门网站推荐
- 协同过滤算法
- 个性化推荐引擎
- 推荐历史记录

#### 📡 API功能

- RESTful API设计
- 请求速率限制
- 响应缓存
- 批量操作支持
- 版本控制
- WebSocket实时通知

#### 🔒 安全性

- 防CSRF攻击
- SQL注入防护
- XSS防护
- 密码哈希存储
- API请求验证
- 敏感数据加密

#### 📦 导入/导出

- 支持标准书签格式导入(HTML)
- 多种格式导出
- 批量导入导出
- 导入冲突处理
- 自动分类

#### 🔒 安全框架

项目采用多层次安全防护策略：

1. **身份验证与授权**
   - JWT基础上增加刷新令牌机制
   - 支持2FA双因素认证（可选）
   - 基于RBAC模型的精细权限控制
   - API权限基于OAuth2.0范围(scopes)

2. **数据安全**
   - 敏感数据使用AES-256加密存储
   - 密码使用Argon2id算法加盐哈希
   - 传输层采用TLS 1.3加密
   - 实现数据脱敏和隐私控制

3. **请求安全**
   - 全局请求速率限制（每IP 100次/分钟）
   - 敏感操作单独限流（登录尝试10次/小时）
   - CSRF保护与SameSite Cookie策略
   - 内容安全策略(CSP)防御XSS

4. **监控与审计**
   - 安全事件日志中心化存储
   - 可疑操作实时告警
   - 定期安全扫描和渗透测试
   - 完整的用户操作审计跟踪

#### 🔄 多级缓存策略

系统实现了多级缓存策略以优化性能：

1. **浏览器缓存**
   - 静态资源使用长期缓存(max-age=31536000)
   - 配合内容哈希文件名实现版本控制
   - 利用Service Worker缓存API响应

2. **应用级缓存**
   - 用户偏好和设置缓存在LocalStorage
   - 书签数据使用IndexedDB进行离线存储
   - 使用Workbox实现请求缓存策略

3. **服务端缓存**
   - Redis缓存用户会话和认证信息(TTL=24小时)
   - 频繁访问的书签数据缓存(TTL=10分钟)
   - 搜索结果和聚合查询缓存(TTL=5分钟)
   - 采用缓存预热策略减少冷启动影响

4. **缓存同步机制**
   - 数据变更时通过WebSocket触发缓存失效
   - 使用基于版本的缓存键避免雪崩效应
   - 实现后台异步缓存重建流程

## 🔄 前后端集成方案

本项目采用前后端分离架构，同时保持前后端在同一代码仓库中管理，具体集成方案如下：

### 开发环境

- Django后端运行在 `localhost:8000`
- Vue3前端运行在 `localhost:5173`（Vite开发服务器）
- 使用Vite的代理功能将API请求转发到Django后端

### 生产环境

- Django作为API服务器和静态文件服务器
- Vue3打包后的静态文件由Django提供服务
- 使用Nginx作为反向代理，处理静态资源缓存和请求转发

### 前后端通信

- 使用REST API进行前后端通信
- 请求URL统一前缀为 `/api/v1/`
- 使用JWT进行用户认证
- API文档通过Swagger/ReDoc自动生成

### API版本控制策略

项目采用严格的API版本控制策略，确保系统可长期演进：

1. **版本标识方式**
   - 主要采用URL路径版本标识：`/api/v1/`, `/api/v2/`
   - 辅助采用Accept头部版本：`Accept: application/vnd.winnie-nav.v1+json`

2. **兼容性保证**
   - 遵循语义化版本控制(SemVer)
   - 次要版本保持向后兼容性
   - 主要版本可能包含不兼容变更

3. **API生命周期管理**
   - 新API特性先在Beta端点发布：`/api/v2-beta/`
   - 弃用API会继续支持至少6个月
   - 弃用API返回Deprecation警告头部

4. **文档策略**
   - 所有版本的API都提供独立文档
   - 使用OpenAPI规范自动生成文档
   - 变更日志详细记录API变化

## 🧩 组件设计

项目使用模块化的组件设计，主要包括：

### 前端核心组件

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

## 🗄️ 数据模型设计

### 后端主要模型

```python
# backend/apps/accounts/models.py
from django.contrib.auth.models import AbstractUser
from django.db import models

class User(AbstractUser):
    """扩展Django默认用户模型"""
    avatar = models.ImageField(upload_to='avatars/', null=True, blank=True)
    theme = models.CharField(max_length=20, default='light')
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    
    class Meta:
        verbose_name = '用户'
        verbose_name_plural = '用户'

# backend/apps/categories/models.py
class Category(models.Model):
    """书签分类模型"""
    name = models.CharField(max_length=100)
    icon = models.CharField(max_length=100, null=True, blank=True)
    color = models.CharField(max_length=20, null=True, blank=True)
    order = models.IntegerField(default=0)
    parent = models.ForeignKey('self', null=True, blank=True, 
                               on_delete=models.CASCADE, related_name='children')
    user = models.ForeignKey('accounts.User', on_delete=models.CASCADE, related_name='categories')
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    
    class Meta:
        verbose_name = '分类'
        verbose_name_plural = '分类'
        ordering = ['order', 'name']
        unique_together = [['name', 'user']]

# backend/apps/bookmarks/models.py
class Bookmark(models.Model):
    """书签模型"""
    title = models.CharField(max_length=255)
    url = models.URLField()
    icon = models.CharField(max_length=255, null=True, blank=True)
    description = models.TextField(null=True, blank=True)
    category = models.ForeignKey('categories.Category', on_delete=models.CASCADE, 
                                 related_name='bookmarks')
    user = models.ForeignKey('accounts.User', on_delete=models.CASCADE, 
                             related_name='bookmarks')
    tags = models.ManyToManyField('Tag', blank=True, related_name='bookmarks')
    order = models.IntegerField(default=0)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    clicks = models.IntegerField(default=0)
    last_clicked = models.DateTimeField(null=True, blank=True)
    
    class Meta:
        verbose_name = '书签'
        verbose_name_plural = '书签'
        ordering = ['order', 'title']
```

### 前端数据结构

```typescript
// frontend/src/types/bookmark.ts

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

## 🛠️ 开发指南

### 前端开发

#### 创建新项目

如果你想从头开始一个新项目，可以使用以下命令：

```bash
# 使用 npm
npm create vite@latest frontend -- --template vue-ts

# 或使用 yarn
yarn create vite frontend --template vue-ts

# 或使用 pnpm
pnpm create vite frontend --template vue-ts
```

#### 安装前端核心依赖

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

#### 添加新组件

1. 在 `frontend/src/components` 目录下创建新的组件文件
2. 使用 Vue3 的 `<script setup>` 语法编写组件
3. 在需要的地方导入并使用该组件

#### 前端状态管理优化

为保证大数据量下的前端性能，项目采用以下状态管理优化策略：

1. **状态分割**
   - 将状态按领域和更新频率分为多个store
   - 核心状态：`userStore`, `settingsStore`
   - 数据状态：`bookmarkStore`, `categoryStore`
   - 视图状态：`uiStore`, `searchStore`

2. **选择性状态订阅**
   - 组件仅订阅所需的最小状态子集
   - 使用Pinia的`storeToRefs`细粒度解构状态
   - 实现`createSharedComposable`避免重复订阅

3. **大数据集处理**
   - 分页加载书签数据(每页50条)
   - 虚拟滚动渲染长列表(`vue-virtual-scroller`)
   - 使用`shallowRef`减少深层响应开销

4. **持久化与预加载**
   - 关键状态使用`pinia-plugin-persistedstate`持久化
   - 预加载常用数据减少初始加载时间
   - 使用IndexedDB存储大型数据集

5. **性能监控**
   - 集成Vue Devtools性能分析
   - 监控状态变更频率和组件重渲染
   - 实现自定义性能标记跟踪关键操作

#### 前端样式开发

1. 优先使用 Tailwind CSS 的原子类
2. 对于复杂样式，可在组件内使用 `<style>` 块
3. 全局样式定义在 `frontend/src/styles` 目录下

### 后端开发

#### 创建新Django项目

```bash
# 创建Django项目
django-admin startproject config .

# 创建应用
python manage.py startapp accounts
python manage.py startapp bookmarks
python manage.py startapp categories
```

#### 安装后端核心依赖

```bash
# 安装基础依赖
pip install django djangorestframework psycopg2-binary python-dotenv

# 安装JWT认证
pip install djangorestframework-simplejwt

# 安装Swagger文档
pip install drf-yasg

# 安装Celery
pip install celery redis
```

#### 开发新API

1. **定义模型**:

```python
# apps/example/models.py
from django.db import models

class Example(models.Model):
    name = models.CharField(max_length=100)
    description = models.TextField(blank=True)
    created_at = models.DateTimeField(auto_now_add=True)
```

2. **创建序列化器**:

```python
# apps/example/serializers.py
from rest_framework import serializers
from .models import Example

class ExampleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Example
        fields = ['id', 'name', 'description', 'created_at']
        read_only_fields = ['created_at']
```

3. **编写视图**:

```python
# apps/example/views.py
from rest_framework import viewsets
from .models import Example
from .serializers import ExampleSerializer

class ExampleViewSet(viewsets.ModelViewSet):
    queryset = Example.objects.all()
    serializer_class = ExampleSerializer
    
    def get_queryset(self):
        # 只返回当前用户的数据
        return self.queryset.filter(user=self.request.user)
```

4. **配置URL**:

```python
# apps/example/urls.py
from django.urls import path, include
from rest_framework.routers import DefaultRouter
from .views import ExampleViewSet

router = DefaultRouter()
router.register('examples', ExampleViewSet)

urlpatterns = [
    path('', include(router.urls)),
]
```

### 前后端集成开发流程

#### 前端API请求配置

在 `frontend/src/services/api.ts` 中配置API请求:

```typescript
import axios from 'axios';

const api = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL || '/api/v1',
  timeout: 10000,
  headers: {
    'Content-Type': 'application/json',
  },
});

// 请求拦截器 - 添加认证Token
api.interceptors.request.use(
  (config) => {
    const token = localStorage.getItem('token');
    if (token) {
      config.headers.Authorization = `Bearer ${token}`;
    }
    return config;
  },
  (error) => Promise.reject(error)
);

export default api;
```

#### Vite代理配置

在 `frontend/vite.config.ts` 中添加:

```typescript
export default defineConfig({
  // ...其他配置
  server: {
    proxy: {
      '/api': {
        target: 'http://localhost:8000',
        changeOrigin: true,
      }
    }
  }
});
```

### 调试技巧

#### 前端调试

1. **Vue DevTools**：使用Vue DevTools浏览器扩展进行组件和状态调试
2. **移动设备预览**：使用Chrome DevTools的设备模拟器
3. **调试日志**：创建调试工具模块记录日志

#### 后端调试

1. **Django Debug Toolbar**：用于显示SQL查询和性能信息
2. **Django Logging**：配置日志系统记录请求和错误
3. **DRF Browsable API**：利用DRF的可浏览API进行接口测试

### 性能优化建议

#### 前端优化

1. **组件懒加载**：使用Vue Router的动态导入
2. **列表虚拟化**：对于长列表，使用虚拟滚动技术
3. **图片优化**：使用适当尺寸的图片，懒加载图片
4. **代码分割**：使用动态导入拆分代码包
5. **Service Worker缓存**：合理配置PWA缓存策略

#### 后端优化

1. **查询优化**：使用select_related和prefetch_related减少数据库查询
2. **缓存**：使用Redis缓存常用数据
3. **分页**：所有列表API实现分页
4. **异步任务**：使用Celery处理耗时操作
5. **数据库索引**：为常用查询字段创建索引

## 📦 依赖管理策略

项目采用严格的依赖版本管理策略，确保构建稳定性和安全性：

### 依赖锁定机制

1. **前端依赖锁定**
   - 使用`package-lock.json`(npm)或`yarn.lock`(yarn)锁定精确版本
   - 构建过程验证依赖完整性(hash校验)
   - 定期更新基础库到最新次要版本

2. **后端依赖锁定**
   - 使用`requirements.txt`锁定精确版本号
   - 通过`pip-compile`自动管理依赖树
   - 生产环境使用wheel包加速部署

### 依赖更新流程

1. **安全更新**
   - 集成GitHub Dependabot自动检测安全漏洞
   - 安全漏洞修复24小时内响应
   - 关键安全问题优先热修复

2. **常规更新**
   - 每月执行依赖更新评估
   - 次要版本自动更新(非破坏性)
   - 主要版本更新需完整测试验证

3. **依赖审计**
   - 新依赖引入需安全评审流程
   - 依赖规模和传递依赖数量控制
   - 定期执行`npm audit`和`safety check`

## 🚀 部署指南

### 使用Docker和Nginx部署

1. **构建前端**：

```bash
cd frontend
npm run build
```

2. **配置Docker Compose**：

```yaml
# docker-compose.prod.yml
version: '3'

services:
  db:
    image: postgres:14
    volumes:
      - postgres_data:/var/lib/postgresql/data/
    env_file:
      - ./.env.prod
    restart: always
    
  redis:
    image: redis:7
    volumes:
      - redis_data:/data
    restart: always
  
  web:
    build:
      context: .
      dockerfile: ./backend/docker/Dockerfile
    volumes:
      - static_volume:/app/staticfiles
      - media_volume:/app/media
    depends_on:
      - db
      - redis
    env_file:
      - ./.env.prod
    restart: always
    command: gunicorn config.wsgi:application --bind 0.0.0.0:8000
  
  nginx:
    image: nginx:1.23
    ports:
      - 80:80
      - 443:443
    volumes:
      - static_volume:/app/staticfiles
      - media_volume:/app/media
      - ./backend/docker/nginx/conf.d:/etc/nginx/conf.d
      - ./backend/docker/nginx/ssl:/etc/nginx/ssl
    depends_on:
      - web
    restart: always

volumes:
  postgres_data:
  redis_data:
  static_volume:
  media_volume:
```

3. **启动生产环境**：

```bash
docker-compose -f docker-compose.prod.yml up -d
```

### 容器化配置与管理

系统容器化配置针对可靠性、可监控性和资源效率进行了优化：

1. **资源限制**

```yaml
# 资源限制示例
services:
  web:
    deploy:
      resources:
        limits:
          cpus: '1'
          memory: 1G
        reservations:
          cpus: '0.5'
          memory: 512M
```

2. **健康检查**

```yaml
# 健康检查配置
services:
  web:
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8000/health/"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 40s
```

3. **日志管理**

```yaml
# 日志配置
services:
  web:
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"
```

4. **监控集成**

系统与Prometheus和Grafana集成，提供全面监控：

- 容器资源使用率监控
- 应用层健康指标监控
- 自定义业务指标监控
- 预设告警规则和面板

5. **滚动更新策略**

```yaml
# 更新策略配置
services:
  web:
    deploy:
      update_config:
        parallelism: 2
        delay: 10s
        order: start-first
```

## 🔄 CI/CD 流程

项目实现了完整的CI/CD流程，确保代码质量和部署自动化：

### GitHub Actions 工作流

1. **代码质量检查**

```yaml
# 代码质量检查工作流示例
name: Code Quality

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main, develop ]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install black isort flake8
      - name: Check code style
        run: |
          black --check backend
          isort --check backend
          flake8 backend
```

2. **自动化测试**

```yaml
# 测试工作流示例
name: Tests

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main, develop ]

jobs:
  test:
    runs-on: ubuntu-latest
    services:
      postgres:
        image: postgres:14
        env:
          POSTGRES_PASSWORD: postgres
          POSTGRES_USER: postgres
          POSTGRES_DB: test_db
        ports:
          - 5432:5432
    steps:
      - uses: actions/checkout@v3
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r backend/requirements/development.txt
      - name: Run tests
        run: |
          cd backend
          pytest
```

3. **自动部署流程**

```yaml
# 部署工作流示例
name: Deploy

on:
  push:
    branches: [ main ]
    tags: [ 'v*' ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build and push Docker images
        uses: docker/build-push-action@v3
        with:
          context: .
          push: true
          tags: |
            ghcr.io/jackEngineer/winnie-nav:latest
            ghcr.io/jackEngineer/winnie-nav:${{ github.ref_name }}
      - name: Deploy to production
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.HOST }}
          username: ${{ secrets.USERNAME }}
          key: ${{ secrets.SSH_KEY }}
          script: |
            cd /opt/winnie-nav
            docker-compose pull
            docker-compose up -d
```

### 发布流程

1. **环境阶段**
   - 开发(Development): 开发人员本地环境和集成测试环境
   - 测试(Staging): 功能测试和性能测试环境
   - 生产(Production): 用户访问的正式环境

2. **发布策略**
   - 采用蓝绿部署策略减少停机时间
   - 特性标志(Feature Flags)控制功能渐进式发布
   - 灰度发布新功能，按用户比例逐步开放

3. **回滚机制**
   - 自动化回滚触发条件(错误率、响应时间阈值)
   - 数据库变更设计可回滚方案
   - 保留历史版本镜像用于紧急回滚

## 📝 贡献指南

1. Fork 本仓库
2. 创建你的特性分支 (`git checkout -b feature/amazing-feature`)
3. 提交你的更改 (`git commit -m 'Add some amazing feature'`)
4. 推送到分支 (`git push origin feature/amazing-feature`)
5. 开启一个 Pull Request

### 代码规范

- 前端: 遵循 [Vue 风格指南](https://cn.vuejs.org/style-guide/)
- 后端: 遵循 [PEP 8](https://peps.python.org/pep-0008/) 和 [Django编码风格](https://docs.djangoproject.com/en/dev/internals/contributing/writing-code/coding-style/)
- 使用 ESLint 和 Prettier 保持前端代码风格一致
- 使用 Black 和 isort 保持后端代码风格一致
- 提交信息遵循 [Conventional Commits](https://www.conventionalcommits.org/zh-hans/) 规范

### 测试

在提交代码前，请确保：

1. 运行并通过所有前端测试

   ```bash
   cd frontend
   npm run test
   ```

2. 运行并通过所有后端测试

   ```bash
   cd backend
   pytest
   ```

3. 检查代码风格

   ```bash
   # 前端
   cd frontend
   npm run lint
   
   # 后端
   cd backend
   black . && isort .
   ```

## ❓ 常见问题解答

### Q: 如何添加新的书签分类？

A: 在设置页面中，点击"分类管理"，然后点击"添加分类"按钮。填写分类名称和选择图标后保存即可。

### Q: 数据存储在哪里？

A: 用户数据存储在后端数据库中。同时，前端会在本地存储部分数据以提升离线使用体验。

### Q: 如何导出我的书签数据？

A: 在设置页面中，点击"数据管理"，然后点击"导出数据"按钮，将生成一个JSON文件供你下载。

### Q: 如何更改主题颜色？

A: 在设置页面中，点击"主题设置"，选择预设主题或自定义颜色方案。

### Q: 忘记密码怎么办？

A: 在登录页面点击"忘记密码"，通过注册邮箱接收重置密码链接。

## 📄 许可证

本项目基于 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

## 📊 版本历史

- **v0.1.0** - 初始版本
  - 基本书签管理功能
  - 分类展示
  - 本地存储数据

## 📞 联系方式

- 项目维护者: [Jack Lee](mailto:j23klee@gmail.com)
- 项目主页: [Winnie-nav](https://github.com/JackEngineer/Winnie-nav)

---

<p align="center">Made with ❤️ for better mobile browsing</p>
