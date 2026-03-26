# 游戏服务全栈管理系统 (Game Service Management System)

[![Node.js Version](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen)](https://nodejs.org/)
[![React Version](https://img.shields.io/badge/react-18.x-blue)](https://react.dev/)
[![MySQL](https://img.shields.io/badge/mysql-8.0-orange)](https://www.mysql.com/)
[![License](https://img.shields.io/badge/license-ISC-green)](LICENSE)

## 📖 项目简介

本项目是一个基于 **React 18 + Node.js (Express) + MySQL** 构建的高性能游戏服务管理平台。系统采用全栈 TypeScript 开发，针对游戏约玩、礼物互动及财务结算等场景提供了完整的解决方案。

系统深度集成了 **Role-Based Access Control (RBAC)** 权限体系，为**管理员**、**客服**及**玩家**三方角色提供独立的交互终端，支持实时通知、在线考勤、财务审核及大数据面板展示。

---

## ✨ 核心特性

### 1. 多角色终端 (Tri-Terminal System)
*   **管理员端 (Admin):** 掌控全局。包含用户权限分配、游戏/礼物库配置、财务提现终审、系统操作日志审计及全站数据可视化看板。
*   **客服端 (Customer Service):** 业务核心。支持在线/忙碌状态切换、订单实时接单、考勤打卡、个人收益统计及提现申请。
*   **玩家端 (Player):** 消费中心。浏览游戏大神、下单约玩、赠送虚拟礼物、个人资产管理及历史订单追踪。

### 2. 财务与订单系统
*   **资金流转:** 完整的充值、消费、分润及提现逻辑，确保每一笔账单可追溯。
*   **提现工作流:** 客服发起申请 -> 管理员后台多级审核 -> 自动/手动结算。
*   **礼物系统:** 支持动态配置礼物属性，绑定不同游戏的消费系数。

### 3. 实时交互能力
*   **Socket.io 集成:** 实现系统级消息秒级推送（如新订单提醒、审核状态变更）。
*   **考勤监控:** 实时记录客服在线时长，自动生成考勤月报。

### 4. 工程化实践
*   **全栈 TypeScript:** 严格的类型定义，减少运行时错误。
*   **组件化开发:** 基于 Ant Design 5.0 深度定制，UI 风格现代且统一。
*   **安全防护:** 采用 JWT 状态保持、BCrypt 强哈希加密存储、防 SQL 注入设计。

---

## 🚀 技术栈

### 前端 (Frontend)
*   **框架:** React 18 (Hooks)
*   **构建工具:** Vite
*   **UI 组件库:** Ant Design 5.x
*   **样式:** Tailwind CSS + Framer Motion (动画)
*   **状态管理:** React Context API + Hooks
*   **网络通信:** Axios + Socket.io-client

### 后端 (Backend)
*   **运行环境:** Node.js 20+
*   **框架:** Express 5.0 (Next-Gen)
*   **数据库:** MySQL 8.0 (驱动: mysql2)
*   **身份验证:** JSON Web Token (JWT)
*   **文件处理:** Multer (图片/素材上传)

---

## 📂 项目结构

```text
├── frontend/               # 前端项目根目录
│   ├── src/
│   │   ├── api/           # API 请求封装
│   │   ├── components/    # 高复用业务组件
│   │   ├── contexts/      # 全局状态管理 (Auth, Notification, Attendance)
│   │   ├── hooks/         # 自定义 React Hooks
│   │   └── pages/         # 页面级组件 (分类存放不同角色页面)
├── backend/                # 后端项目根目录
│   └── server/
│       ├── src/
│       │   ├── dao/       # 数据库访问层
│       │   ├── routes/    # 路由定义
│       │   ├── services/  # 核心业务逻辑
│       │   └── middleware/# 权限/日志中间件
│       └── sql/           # 数据库结构及迁移脚本
├── uploads/                # 动态上传资源 (头像/二维码/游戏素材)
└── tests/                  # 接口测试与业务流自动化测试脚本
```

---

## 🛠️ 快速上手

### 1. 数据库准备
1. 创建数据库 `author_center`。
2. 导入根目录下的 `database_complete.sql`。
3. 如果需要初始测试数据，可运行 `backend/sql/database_enhanced_with_real_data.sql`。

### 2. 后端配置
```bash
cd backend/server
npm install
# 修改 .env 文件中的数据库连接信息 (DB_USER, DB_PASS 等)
npm run dev
```

### 3. 前端配置
```bash
cd frontend
npm install
npm run dev
```

---

## 🌐 部署指南

项目支持多种部署方案，推荐使用 **宝塔面板 (BT Panel)** 进行生产环境快速部署：

1.  **环境要求:** 安装 Nginx 1.20+, MySQL 8.0, Node.js 18+ (使用 PM2 管理)。
2.  **前端构建:** 运行 `npm run build` 生成 `dist` 目录，配置 Nginx 静态托管。
3.  **反向代理:** 配置 Nginx 将 `/api` 路径转发至后端 3000 端口。
4.  **进程守护:** 使用 PM2 启动后端服务 `pm2 start src/index.ts --interpreter ts-node`。

*详细步骤请参考 [宝塔面板部署指南.md](./宝塔面板部署指南.md)*

---

## 📜 许可证

本项目基于 **ISC License** 开源。
