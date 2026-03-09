# README - BioApple 生物信息学分析平台

## 项目简介

BioApple 是一个支持多应用拓展的生物信息学分析平台，提供文件上传、任务管理、系统监控等功能。

## 功能特性

- ✅ 用户登录/注册
- ✅ 用户管理（管理员功能）
- ✅ 文件上传（支持分片上传）
- ✅ 任务管理（创建、查看、重分析、删除）
- ✅ 系统监控（CPU、内存、磁盘使用情况）
- ✅ 任务日志记录
- ✅ 自动识别样本类型（单端/双端）
- ✅ 自动识别测序平台（BGI/Illumina）
- ✅ 全局串行任务执行
- ✅ 服务器关机/重启功能
- ✅ 数据清理功能（3/6/12个月）

## 技术栈

### 后端
- FastAPI - Web 框架
- Celery - 分布式任务队列
- Redis - 消息队列和缓存
- PostgreSQL - 关系型数据库
- SQLAlchemy - ORM
- Tus.io - 分片上传协议

### 前端
- Vue.js 3 - 前端框架
- Element Plus - UI 组件库
- Vite - 构建工具

## 快速开始

### 环境要求

- Python 3.8+
- Node.js 16+
- Redis（可选，用于任务队列）
- PostgreSQL（或使用 SQLite）

### 安装步骤

1. 克隆项目或进入项目目录

2. 运行启动脚本（Linux/Mac）：
```bash
./start.sh
```

或运行启动脚本（Windows）：
```cmd
start.bat
```

3. 访问 http://localhost:8000

### 手动安装

#### 后端安装

```bash
# 创建虚拟环境
python -m venv venv

# 激活虚拟环境
# Linux/Mac:
source venv/bin/activate
# Windows:
venv\Scripts\activate

# 安装依赖
pip install -r backend/requirements.txt

# 初始化数据库
cd backend
python database.py
```

#### 前端安装

```bash
cd frontend
npm install
npm run dev
```

## 配置文件

项目使用 `.env` 文件进行配置，参考 `.env.example`：

```env
# 服务器配置
SERVER_HOST=0.0.0.0
SERVER_PORT=8000

# 文件上传配置
UPLOAD_DIR=/path/to/uploads
RESULT_DIR=/path/to/results
REFERENCE_DIR=/path/to/reference

# 数据库配置
DATABASE_URL=postgresql+asyncpg://username:password@localhost:5432/bio_apple

# Redis 配置
REDIS_URL=redis://localhost:6379/0

# JWT 配置
SECRET_KEY=your-secret-key-change-in-production
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30

# 日志配置
LOG_LEVEL=INFO
LOG_FILE=/path/to/logs/app.log
```

## 项目结构

```
AI_code/
├── backend/                  # 后端代码
│   ├── api/                 # API 路由
│   │   └── v1/             # API v1
│   ├── models.py            # 数据库模型
│   ├── config.py            # 配置文件
│   ├── database.py          # 数据库连接
│   ├── auth.py              # 认证模块
│   ├── tasks.py             # Celery 任务
│   ├── redis_client.py      # Redis 客户端
│   ├── main.py              # 主应用
│   └── requirements.txt     # Python 依赖
├── frontend/                # 前端代码
│   ├── src/
│   │   ├── views/          # 页面组件
│   │   ├── api/            # API 调用
│   │   ├── store/          # 状态管理
│   │   └── router/         # 路由配置
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
├── start.sh                 # Linux/Mac 启动脚本
├── start.bat                # Windows 启动脚本
├── stop.sh                  # 停止脚本
└── README.md
```

## 使用说明

### 用户登录

- 默认管理员账户需要在数据库中手动创建
- 用户可以注册新账户

### 文件上传

1. 进入"文件上传"页面
2. 选择 FASTQ 文件（支持 .fastq, .fq, .gz 格式）
3. 配置任务参数（任务名称、样本类型、测序平台）
4. 提交任务

### 任务管理

- 查看任务列表和状态
- 查看任务详情和日志
- 重新运行失败的任务
- 删除不需要的任务

### 系统监控

- 查看系统信息（CPU、内存、磁盘）
- 查看运行进程
- 管理员可以清理旧数据
- 管理员可以重启/关闭服务器

## 开发说明

### 后端开发

```bash
cd backend
# 运行开发服务器
uvicorn main:app --reload
```

### 前端开发

```bash
cd frontend
# 运行开发服务器
npm run dev
```

## 许可证

MIT License

## 联系方式

如有问题，请联系管理员。
