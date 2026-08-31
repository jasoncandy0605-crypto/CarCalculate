# 🚗 CarCalculate

**Personal Finance AI Assistant with Car-Themed Visual Design**

CarCalculate 是一个以汽车为主题的个人财务AI智能体。它帮助用户记录日常收支、管理储蓄、分析消费习惯，并提供基于AI的智能财务建议。

## 🎯 核心功能

- 📊 **财务追踪** - 记录收入、支出，管理多种分类
- 💰 **储蓄管理** - 创建和追踪个性化储蓄目标
- 📈 **数据分析** - 查看每日/每周/每月财务概况
- 🤖 **AI智能体** - 基于真实数据的消费分析和建议
- 🚗 **汽车主题** - 高级汽车摄影+现代UI设计
- 🎨 **视觉设计** - 明亮暖色系，高级生活方式感

## ⚠️ 重要设计原则

### 不是什么
❌ 买车存钱工具  
❌ 汽车贷款计算器  
❌ 汽车预算工具

### 是什么
✅ 个人财务管理平台  
✅ 汽车视觉主题系统  
✅ AI财务分析助手

### 汽车图片规则【绝对硬性要求】
- ✅ 必须是真实汽车照片
- ✅ 使用前必须验证：品牌、车型、代际、年份、版本
- ❌ 禁止AI生成图片
- ❌ 禁止使用AI生成的图片

## 🏗️ 项目结构

```
CarCalculate/
├── backend/                    # Node.js + Express + TypeScript
│   ├── src/
│   │   ├── models/            # Mongoose数据模型
│   │   ├── controllers/       # 业务逻辑
│   │   ├── services/          # 服务层
│   │   ├── middlewares/       # 中间件
│   │   ├── routes/            # API路由
│   │   ├── utils/             # 工具函数
│   │   ├── config/            # 配置文件
│   │   └── index.ts           # 入口文件
│   ├── package.json
│   ├── tsconfig.json
│   └── Dockerfile
│
├── frontend/                   # React + TypeScript + Tailwind
│   ├── src/
│   │   ├── components/        # 可复用组件
│   │   ├── pages/             # 页面
│   │   ├── hooks/             # React钩子
│   │   ├── services/          # API服务
│   │   ├── types/             # TypeScript类型
│   │   ├── utils/             # 工具函数
│   │   ├── styles/            # 全局样式
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── public/                # 静态资源
│   ├── package.json
│   ├── vite.config.ts
│   ├── tsconfig.json
│   ├── tailwind.config.js
│   └── Dockerfile
│
├── .github/workflows/          # CI/CD
├── docker-compose.yml
├── .gitignore
└── README.md
```

## 🛠️ 技术栈

### 后端
- **Runtime**: Node.js
- **Framework**: Express.js
- **Language**: TypeScript
- **Database**: MongoDB
- **Authentication**: JWT
- **AI Integration**: OpenAI API

### 前端
- **Framework**: React 18
- **Language**: TypeScript
- **Bundler**: Vite
- **Styling**: Tailwind CSS
- **UI**: Headless UI
- **State**: TanStack Query + Zustand
- **HTTP Client**: Axios

## 📱 页面结构

| 页面 | 功能 |
|------|------|
| 首页 Dashboard | 汽车Hero + 余额 + 本月收支 + AI洞察 |
| 交易 Transactions | 历史交易列表，支持筛选和搜索 |
| 记账 Add Transaction | 快速记录收入/支出 |
| 分析 Analytics | 消费趋势、分类统计 |
| AI助手 AI Copilot | 财务问答和建议 |
| 车库 Garage | 选择主题车型、管理视觉风格 |
| 设置 Settings | 用户设置、偏好配置 |

## 🎨 UI/UX 设计方向

### 色彩系统
- 主色：温暖米白、奶油色
- 辅助色：淡米色、暖橙、浅金色、柔和棕色
- 文字：深色用于对比

### 设计原则
- 明亮、温暖、高级、现代
- 大卡片、圆角、柔和阴影
- 充足留白
- 移动端优先响应式设计
- 高级汽车生活方式App的感觉

## 🚀 快速开始

### 前置要求
- Node.js >= 18
- MongoDB >= 5.0
- Docker & Docker Compose（可选）

### 本地开发

```bash
# 克隆项目
git clone https://github.com/jasoncandy0605-crypto/CarCalculate.git
cd CarCalculate

# 使用Docker Compose
docker-compose up -d

# 或手动安装

# 后端
cd backend
npm install
npm run dev

# 前端（新终端）
cd frontend
npm install
npm run dev
```

### 环境配置

后端 `.env`:
```
MONGODB_URI=mongodb://localhost:27017/carcalculate
JWT_SECRET=your-secret-key
OPENAI_API_KEY=your-openai-key
NODE_ENV=development
PORT=5000
```

前端 `.env.local`:
```
VITE_API_URL=http://localhost:5000
```

## 📊 数据模型

### User
```typescript
{
  _id: ObjectId
  email: string
  password: string (hashed)
  name: string
  currency: string (e.g., "USD", "MYR")
  monthlyIncome: number
  selectedVehicle: ObjectId (ref: Vehicle)
  theme: string
  createdAt: Date
  updatedAt: Date
}
```

### Transaction
```typescript
{
  _id: ObjectId
  userId: ObjectId
  type: "income" | "expense"
  amount: number
  category: string
  date: Date
  note: string
  paymentMethod: string
  createdAt: Date
  updatedAt: Date
}
```

### SavingsGoal
```typescript
{
  _id: ObjectId
  userId: ObjectId
  name: string
  targetAmount: number
  currentAmount: number
  deadline: Date
  description: string
  priority: "low" | "medium" | "high"
  createdAt: Date
  updatedAt: Date
}
```

### Vehicle
```typescript
{
  _id: ObjectId
  brand: string
  model: string
  generation: string
  year: number
  variant: string
  imageUrl: string
  imageSource: string
  verificationStatus: "pending" | "verified" | "rejected"
  verificationNotes: string
  createdAt: Date
  updatedAt: Date
}
```

## 🤖 AI财务分析模块

AI助手基于用户真实财务数据提供：
- 消费趋势分析
- 支出异常检测
- 储蓄进度评估
- 个性化消费建议
- 预测月底余额

**语气特点**：自然、友好、聪明、简洁，像一个真正懂你的个人财务助手。

## 🚗 汽车主题内容

用户可以在"车库"选择不同的真实汽车作为应用主题，每个车型都经过严格验证。

## 📄 许可证

MIT

## 👤 作者

jasoncandy0605-crypto

---

**开发进度**: 项目初始化中 🚀
