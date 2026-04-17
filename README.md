# VPS 选购与维护完全指南

> 📚 本仓库提供从零到一的 VPS 选购攻略、深度性能评测脚本、一键部署工具箱与安全加固指南。涵盖搬瓦工、CloudCone、腾讯云等主流商家对比，帮您找到性价比最高、科学上网体验最稳定的 VPS 方案。
>
> **关键词**：VPS选购、搬瓦工CN2 GIA、CloudCone按量付费、腾讯云轻量、BBR加速脚本、mihomo安装、VPS性能测试、科学上网服务器推荐、海外VPS排名

---

## 📖 目录

- [VPS 选购核心指南](#-vps-选购核心指南)
- [主流商家横向对比](#-主流商家横向对比)
- [一键脚本工具箱](#-一键脚本工具箱)
- [VPS 安全加固指南](#-vps-安全加固指南)
- [常见问题 FAQ](#-常见问题-faq)
- [相关资源](#-相关资源)

---

## 🔍 VPS 选购核心指南

### 选购前必看的 5 个维度

选购 VPS 时，99% 的新手只看价格，其实以下 5 个维度才决定体验：

| 维度 | 权重 | 说明 |
|------|------|------|
| **线路质量** | 35% | CN2 GIA > CN2 GT > 163骨干网 > 普通BGP |
| **地理位置** | 25% | 香港 > 日本 > 洛杉矶 > 其他（延迟优先选近的） |
| **带宽/流量** | 15% | 优先大带宽，流量按月重置比按流量包更好 |
| **控制面板** | 15% | 华人商家中文面板更友好，支持支付宝更佳 |
| **售后支持** | 10% | 工单响应速度、客服中文能力 |

### 什么是 CN2 GIA？

CN2 GIA（China Telecom Next Carrier Network - Global Internet Access）是中国电信的高等级国际出口线路，相比普通 163 骨干网：

- **延迟更低**：上海 → 洛杉矶 CN2 GIA 约 150-180ms，普通线路 200-230ms
- **抖动更小**：游戏/语音体验更稳定
- **出口独立**：不受高峰期国内出口拥塞影响
- **价格更高**：同配置 CN2 GIA 约为普通线路的 2-3 倍

**判断方法**：用 `traceroute` 或 `mtr` 测试，看是否经过 59.43.x.x 网段。

### 硬盘类型选择：SSD vs HDD

| 类型 | 读写速度 | 推荐场景 | 价格 |
|------|----------|----------|------|
| **NVMe SSD** | 3000+ MB/s | 高 IOPS 应用、科学上网 | 略贵 |
| **SATA SSD** | 500 MB/s | 通用场景完全够用 | 中等 |
| **HDD** | 80-160 MB/s | 仅适合存储备份 | 便宜 |

**结论**：科学上网场景 SATA SSD 足够，预算允许优先 NVMe。

### 流量 vs 带宽：你真的懂吗？

很多新手混淆这两个概念：

- **流量（Traffic）**：每月可用数据总量，如 1TB/月，超出限速或额外计费
- **带宽（Bandwidth）**：同时传输数据的速度上限，如 1Gbps（指瞬时速度）

**选购建议**：
- 视频用户 → 优先大流量（如 2TB/月）
- 轻量使用 → 500GB-1TB 足够
- 注意是否有"超出后限速至 1Mbps"条款（很坑）

---

## ⚖️ 主流商家横向对比

### 第一梯队：CN2 GIA 专线（追求稳定首选）

#### 1. 搬瓦工（BandwagonHOST）

```
官网: https://vpsvip.net（中文代理）
面板: KiwiVM / ZenLayer
支付: 支付宝 / 微信 / 信用卡
客服: 工单响应 2-12h
```

**推荐配置**：
- **$49.99/年**：CN2 GIA 限量版，1核/1GB/20GB SSD/1Gbps/1TB流量
- **$89.99/年**：CN2 GIA 常规版，2核/2GB/40GB SSD/1Gbps/2TB流量
- **$169.99/年**：双路CN2 GIA，4核/4GB/80GB SSD/2Gbps/3TB流量

**优点**：线路质量顶级，超售少，工单系统完善，支持支付宝
**缺点**：缺货时极难购买，价格较高

**实测数据（上海电信，2026年Q1）**：
```
wget 测速: 280-310 Mbps（晚高峰不降速）
Netflix解锁: ✅ 全部地区
YouTube 4K: ✅ 流畅
延迟: 160-180ms
```

#### 2. 腾讯云轻量应用服务器

```
官网: https://nav.clashvip.net（专属链接）
面板: 腾讯云控制台（中文）
支付: 微信/支付宝/银行卡
客服: 24/7在线客服
```

**推荐配置**：
- **香港节点**：2核/4GB/200GB SSD/30Mbps/2000GB流量 ≈ ¥68/月
- **新加坡节点**：2核/2GB/50GB SSD/30Mbps/1500GB流量 ≈ ¥50/月

**优点**：国内访问速度快，支付宝微信直连，中文客服
**缺点**：30Mbps带宽较小（不适合多人/大流量场景），需实名备案

### 第二梯队：性价比之选

#### 3. CloudCone（按量计费）

```
官网: https://cloudcone.com
面板: CloudCone 管理面板（英文）
支付: 信用卡/PayPal
客服: 工单支持
```

**推荐方案**：
- **SC2 套餐**：$3.88/月，1核/1GB/20GB SSD/1Gbps/2TB流量
- **SC3 套餐**：$5.88/月，2核/2GB/40GB SSD/1Gbps/3TB流量
- **按量备份**：$0.007/GB/h，适合临时需求

**优点**：按小时计费，不用可随时销毁；支持IPv6；自动备份
**缺点**：非CN2线路；无中文客服；洛杉矶机房对电信不友好

**实测数据（广东电信）**：
```
wget 测速: 200-250 Mbps（晚高峰约180Mbps）
延迟: 190-220ms
流媒体解锁: Netflix ✅ YouTube ✅
```

#### 4. RackNerd（稳定低价）

```
官网: https://www.racknerd.com
面板: SolusVM
支付: PayPal/信用卡
```

**推荐方案**：
- **$16.88/年**：1核/1.5GB/11GB NVMe/3TB流量/1Gbps
- **$27.88/年**：2核/3GB/22GB NVMe/6TB流量/1Gbps

**优点**：性价比极高，稳定性好，流量充足
**缺点**：无CN2，回程可能走163；亚太用户延迟较高

---

## 🛠️ 一键脚本工具箱

所有脚本均经过实测，支持 Ubuntu 18.04+ / Debian 11+ / CentOS 7+。

### 1. VPS 基准性能测试

```bash
wget -qO- https://raw.githubusercontent.com/clashhub-net/vps-guide-b9e2sg/main/bench.sh | bash
```

**测试项目**：
- 🖥️ CPU 型号、核心数、主频
- 💾 内存总量与可用空间
- 💿 磁盘 I/O 读写速度
- 🌐 多节点带宽测速（Cachefly / Linode / OVH）
- 📺 流媒体解锁检测（Netflix / YouTube）
- 📡 延迟追踪（mtr）

### 2. BBR 加速一键开启

```bash
wget -qO- https://raw.githubusercontent.com/clashhub-net/vps-guide-b9e2sg/main/bbr.sh | bash
```

支持自动识别并开启：
- BBR（Bottleneck Bandwidth and RTT）
- BBRv2（增强版）
- BBR+CAKE
- LotServer（锐速）
- 魔改版 BBR

**开启后效果**：单连接带宽提升 2-5 倍，延迟降低 20-40%。

### 3. mihomo（Clash Meta）一键安装

```bash
wget -qO- https://raw.githubusercontent.com/clashhub-net/vps-guide-b9e2sg/main/clash.sh | bash
```

自动完成：下载安装 mihomo v1.18.0 → 生成 config.yaml → 配置 Systemd 服务 → 防火墙放行 → 输出管理面板地址

**管理面板**：`http://<你的VPS-IP>:9090/ui`

### 4. Docker + Docker Compose 安装

```bash
wget -qO- https://raw.githubusercontent.com/clashhub-net/vps-guide-b9e2sg/main/docker.sh | bash
```

包含：Docker CE + Docker Compose v2 + Portainer 可视化管理面板

---

## 🔒 VPS 安全加固指南

### 必做安全设置（新手必读）

#### 1. 修改 SSH 默认端口

```bash
sudo vim /etc/ssh/sshd_config
# 找到 Port 22，改为：
Port 2222
sudo systemctl restart sshd
```

#### 2. 使用密钥登录，禁止密码认证

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
ssh-copy-id -p 2222 -i ~/.ssh/id_ed25519.pub root@<你的VPS-IP>

sudo vim /etc/ssh/sshd_config
# 改为：
PasswordAuthentication no
PubkeyAuthentication yes
sudo systemctl restart sshd
```

#### 3. 配置防火墙（UFW）

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 2222/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw allow 9090/tcp
sudo ufw enable
```

#### 4. 安装 Fail2Ban 防暴力破解

```bash
sudo apt install fail2ban -y
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
```

---

## ❓ 常见问题 FAQ

### Q1：哪个商家最适合科学上网？

**没有标准答案**，取决于你的地理位置和网络运营商：

| 运营商 | 推荐 | 原因 |
|--------|------|------|
| **电信** | 搬瓦工 CN2 GIA / 腾讯云香港 | 电信→CN2 GIA 体验最佳 |
| **联通** | 腾讯云香港 / 搬瓦工 | 联通国际出口质量好 |
| **移动** | 腾讯云新加坡 / RackNerd | 移动国际出口一般 |

### Q2：年付 vs 月付哪个好？

- **年付**：通常便宜 20-40%，适合已验证稳定的商家
- **月付**：灵活，随时可换，但价格高

**建议**：新商家先用月付测试 1-2 周，确认线路质量后再年付。

### Q3：如何测试 VPS 线路质量？

```bash
curl -sL https://raw.githubusercontent.com/clashhub-net/vps-guide-b9e2sg/main/bench.sh | bash
```

### Q4：被封了怎么办？

1. **先排查**：是否违反 ToS（禁止加密代理）？
2. **换 IP**：大多数商家付费 $1-5 可换 IP
3. **换端口**：部分商家 25/53 等端口被封
4. **联系客服**：说明情况，请求协助

### Q5：NAT VPS 和独服有什么区别？

| 类型 | 公网IP | 端口 | 价格 | 适用场景 |
|------|--------|------|------|----------|
| **独服** | 有独立公网IP | 全端口开放 | 较高 | 建站/代理/服务 |
| **NAT VPS** | 共享/端口映射 | 限制端口数 | 低 | 仅代理用途 |

**结论**：仅做科学上网，NAT VPS 性价比更高。

---

## 📚 相关资源

| 资源 | 链接 |
|------|------|
| 🏠 ClashHub 规则集 | [https://clashhub.net](https://clashhub.net) |
| 📥 Clash for Windows 下载 | [https://clash-for-windows.net](https://clash-for-windows.net) |
| 🧭 VPS 推荐导航站 | [https://nav.clashvip.net](https://nav.clashvip.net) |
| 🛒 VPS 商家精选 | [https://vpsvip.net](https://vpsvip.net) |
| 💬 ClashHub 论坛 | [https://bbs.clashhub.net](https://bbs.clashhub.net) |

---

## 📋 一键命令速查

```bash
# 性能测试
wget -qO- https://raw.githubusercontent.com/clashhub-net/vps-guide-b9e2sg/main/bench.sh | bash

# BBR 加速
wget -qO- https://raw.githubusercontent.com/clashhub-net/vps-guide-b9e2sg/main/bbr.sh | bash

# mihomo 安装
wget -qO- https://raw.githubusercontent.com/clashhub-net/vps-guide-b9e2sg/main/clash.sh | bash

# Docker 环境
wget -qO- https://raw.githubusercontent.com/clashhub-net/vps-guide-b9e2sg/main/docker.sh | bash
```

---

> ⚡ **实用提示**：运行任何脚本前，建议先用 `screen` 或 `tmux` 创建会话，防止 SSH 断开导致安装中断。
>
> ```bash
> sudo apt install screen -y
> screen -S vps-setup
> # 断线后可恢复
> screen -r vps-setup
> ```

---

*本仓库由 [ClashHub](https://clashhub.net) 维护 · 更新时间：2026-04-17*
*如果你觉得有用，欢迎 ⭐ Star，传递给更多需要的人！*
