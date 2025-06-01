# MT Photos 照片管理系统

这是一个基于 Docker 的照片管理系统，集成了 MT Photos 及其相关服务，提供强大的照片管理、AI 人脸识别和智能分类功能。

## 功能特点

- 照片管理和浏览
- AI 人脸识别和分析
- 智能照片分类
- GPU 加速支持
- 完整的 Docker 容器化部署

## 系统要求

- Docker 和 Docker Compose
- NVIDIA GPU（用于 AI 功能）
- NVIDIA Container Toolkit

## 快速开始

1. 克隆仓库：
```bash
git clone [repository-url]
cd mt-photos
```

2. 启动服务：
```bash
docker-compose up -d
```

3. 访问服务：
- MT Photos 主界面：http://localhost:8063
- AI 服务：http://localhost:8060
- InsightFace 服务：http://localhost:8066

## 目录结构

- `mt-photos/` - MT Photos 配置和上传目录
- `photos/` - 照片存储目录
- `docker-compose.yml` - Docker 服务配置文件

## 服务说明

- **mt-photos**: 主照片管理服务
- **mt-photos-ai**: AI 分析服务（需要 GPU）
- **insightface**: 人脸识别服务（需要 GPU）
- **socat-redis**: Redis 端口转发服务
- **socat-psql**: PostgreSQL 端口转发服务

## API 服务

### 智能搜索 API
- 服务地址：http://mt-photos-ai:8060
- 认证密钥：mt_photos_ai_extra

### 人脸识别 API
- 服务地址：http://insightface:8066
- 认证密钥：mt_photos_ai_extra

## 数据库连接

### PostgreSQL 连接信息
- 主机：localhost
- 端口：5432
- 用户名：postgres
- 密码：空
- 数据库：postgres

连接示例：
```bash
psql -h localhost -p 5432 -U postgres -d postgres
```

### Redis 连接信息
- 主机：localhost
- 端口：6379
- 密码：空

连接示例：
```bash
redis-cli -h localhost -p 6379
```

## 环境变量

- `TZ`: 时区设置（默认：Asia/Shanghai）
- `API_AUTH_KEY`: AI 服务认证密钥（默认：mt_photos_ai_extra）

## 注意事项

1. 确保系统已安装 NVIDIA 驱动和 NVIDIA Container Toolkit
2. 首次启动时，系统会自动下载所需的 Docker 镜像
3. 建议定期备份 `mt-photos/config` 目录下的配置文件
4. 数据库连接信息仅用于开发和调试，生产环境请修改默认密码
5. API 服务需要在 Docker 网络内部访问，外部访问请使用 localhost 地址

## 许可证

请参考 MT Photos 官方许可证说明。 