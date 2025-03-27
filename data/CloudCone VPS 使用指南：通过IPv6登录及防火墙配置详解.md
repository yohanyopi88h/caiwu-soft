# CloudCone VPS 使用指南：通过IPv6登录及防火墙配置详解

## 前言：为什么选择CloudCone VPS？

原本使用腾讯云服务器的我，由于4M带宽无法满足AList应用需求，转而尝试了CloudCone的高性价比方案：
- **超值配置**：11美元/年
- **超大流量**：每月2T
- **高速带宽**：1Gbps

👉 [【点击查看】2025年最新CloudCone优惠码及特价云服务器方案汇总](https://bit.ly/Cloudcone)

## 一、IPv4连接问题排查

初次使用时发现IPv4无法ping通：
bash
正在 Ping 198.52.**.** 具有 32 字节的数据:
请求超时。
请求超时。
请求超时。
请求超时。

### 解决方案：启用IPv6
1. 登录CloudCone控制面板
2. 进入`Networking`设置
3. 开启`enable ipv6`选项
4. 确认显示为**global**地址

## 二、通过IPv6远程登录教程

### 使用PuTTY连接步骤
1. 在主机名栏输入IPv6地址
2. 使用默认用户名`root`
3. 输入邮件收到的初始密码

### 安全建议
bash
sudo passwd root
New password:
Retype new password:
passwd: password updated successfully

建议首次登录后立即修改密码

## 三、UFW防火墙配置指南

### 基础命令速查
| 功能 | 命令 |
|------|------|
| 查看状态 | `sudo ufw status` |
| 启用防火墙 | `sudo ufw enable` |
| 禁用防火墙 | `sudo ufw disable` |
| 重启防火墙 | `sudo ufw reload` |

### 关键注意事项
⚠️ **必须**在启用防火墙前放行SSH端口：
bash
sudo ufw allow 22/tcp

否则会导致服务器无法连接！

## 四、常见问题解决方案

### 系统兼容性问题
- 低配服务器(内存<1GB)建议使用Ubuntu 20.04
- Ubuntu 22.04可能出现兼容性问题

### 紧急恢复方案
若误操作导致无法连接：
1. 通过CloudCone控制台重装系统
2. 建议选择经过验证的系统版本
3. 可联系24/7在线客服获取支持

## 最佳实践建议
1. 定期检查防火墙规则
2. 重要端口设置双因素验证
3. 建立操作检查清单
4. 考虑使用密钥认证替代密码登录

通过合理配置，CloudCone VPS完全可以满足个人建站、文件存储等多样化需求，是性价比极高的海外服务器选择。