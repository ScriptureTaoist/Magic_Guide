# Mihomo Web UI 配置指南

## 概述

Mihomo 支持多种 Web UI 管理界面，方便可视化管理代理节点和规则。

## 可用的 Web UI

### 1. MetaCubeXD（推荐）

现代化的 Dashboard 界面，功能完善。

- **在线版本**: https://metacubexd.pages.dev/
- **GitHub**: https://github.com/MetaCubeX/metacubexd
- **特点**:
  - 现代化 UI 设计
  - 支持多语言
  - 实时连接监控
  - 规则管理
  - 代理延迟测试

### 2. Yacd

经典的 Dashboard 界面。

- **在线版本**: http://yacd.haishan.me/
- **GitHub**: https://github.com/haishanh/yacd
- **特点**:
  - 轻量级
  - 简洁直观
  - 支持规则查看

### 3. Razord

移动端友好界面。

- **在线版本**: https://razord.top/
- **GitHub**: https://github.com/ClashRazord/razord-web

## 配置方式

### 方式一：本地 UI（推荐）

将 UI 文件部署在服务器本地：

```yaml
# config.yaml
external-controller: 0.0.0.0:9090
external-ui: ui
secret: "your-secret-key"
```

目录结构：

```
/etc/mihomo/
├── config.yaml
└── ui/
    ├── index.html
    └── ...
```

访问地址：`http://服务器IP:9090/ui`

### 方式二：使用在线 UI

无需下载，直接使用在线版本：

```yaml
external-controller: 0.0.0.0:9090
secret: "your-secret-key"
```

访问步骤：
1. 打开 https://metacubexd.pages.dev/
2. 在连接地址输入：`http://服务器IP:9090`
3. 输入密钥（如果设置了 `secret`）

### 方式三：自动下载 UI

配置自动下载：

```yaml
external-controller: 0.0.0.0:9090
external-ui: ui
external-ui-url: "https://github.com/MetaCubeX/metacubexd/archive/refs/heads/gh-pages.zip"
secret: "your-secret-key"
```

首次启动时会自动下载 UI。

## 完整配置示例

```yaml
# 基础配置
mixed-port: 7890
allow-lan: true
mode: rule
log-level: info

# Web UI 配置
external-controller: 0.0.0.0:9090
external-ui: ui
secret: "your-strong-secret"

# 其他配置...
```

## 安全配置

### 1. 设置强密钥

```yaml
secret: "复杂密钥字符串"
```

### 2. 限制访问 IP

```yaml
# 仅允许本地访问
external-controller: 127.0.0.1:9090

# 或允许所有
external-controller: 0.0.0.0:9090
```

### 3. 使用 Nginx 反向代理（推荐）

```nginx
server {
    listen 443 ssl;
    server_name your-domain.com;
    
    ssl_certificate /path/to/cert.pem;
    ssl_certificate_key /path/to/key.pem;
    
    location / {
        auth_basic "Mihomo Dashboard";
        auth_basic_user_file /etc/nginx/.htpasswd;
        
        proxy_pass http://127.0.0.1:9090;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

配置 mihomo：

```yaml
external-controller: 127.0.0.1:9090
secret: "your-secret"
```

### 4. 防火墙配置

```bash
# 仅允许特定 IP 访问
sudo ufw allow from 192.168.1.0/24 to any port 9090

# 或使用 iptables
sudo iptables -A INPUT -p tcp --dport 9090 -s 192.168.1.0/24 -j ACCEPT
```

## 功能说明

### 连接管理

- 查看当前所有连接
- 查看连接的代理节点
- 关闭指定连接

### 代理管理

- 切换代理节点
- 测试节点延迟
- 查看节点信息

### 规则查看

- 查看所有规则
- 规则匹配测试

### 日志查看

- 实时日志
- 日志级别切换

### 配置管理

- 在线修改配置
- 重载配置
- 切换配置文件

## API 接口

Web UI 通过 REST API 与 mihomo 通信：

| 接口 | 说明 |
|------|------|
| GET / | 获取版本信息 |
| GET /logs | 获取日志流 |
| GET /connections | 获取连接列表 |
| DELETE /connections | 关闭所有连接 |
| GET /proxies | 获取代理列表 |
| GET /proxies/:name | 获取代理详情 |
| PUT /proxies/:name | 切换代理 |
| GET /rules | 获取规则列表 |
| GET /configs | 获取配置 |
| PUT /configs | 修改配置 |
| PATCH /configs | 重载配置 |

## 故障排查

### 无法打开 UI

1. 检查服务是否运行：`systemctl status mihomo`
2. 检查端口是否监听：`netstat -tlnp | grep 9090`
3. 检查防火墙规则

### 连接被拒绝

1. 确认 `external-controller` 绑定地址正确
2. 检查密钥是否正确
3. 检查浏览器控制台错误信息

### UI 加载失败

1. 检查 `external-ui` 路径是否正确
2. 确认 UI 文件完整
3. 查看服务日志

## 已包含的 UI

本项目已包含 MetaCubeXD v1.241.2，位于 `ui/` 目录下。
