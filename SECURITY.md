# 安全策略 | Security Policy

## 🔒 支持的版本

我们为以下版本提供安全更新：

| Version | Supported          |
| ------- | ------------------ |
| 3.0.x   | :white_check_mark: |
| 2.x.x   | :white_check_mark: |
| < 2.0   | :x:                |

## 🛡️ 安全最佳实践

### API密钥管理
- **绝不在代码中硬编码API密钥**
- **使用环境变量存储敏感信息**
- **定期轮换API密钥**
- **为API密钥设置最小权限**

### 环境配置
```bash
# 推荐使用环境变量
export OKX_API_KEY="your_api_key"
export OKX_SECRET_KEY="your_secret_key"
export OKX_PASSPHRASE="your_passphrase"

# 或使用.env文件（确保不提交到版本控制）
cp env.example .env
# 编辑.env文件填入实际信息
```

### 文件权限
```bash
# 确保配置文件权限安全
chmod 600 .env
chmod 600 config.py
```

## 🚨 报告安全漏洞

如果您发现安全漏洞，请通过以下方式报告：

### 📧 私人联系
- **邮箱**: security@trading-system.com
- **PGP Key**: [获取公钥](https://keybase.io/tradingsystem)

### 📋 报告内容
请在报告中包含：
1. **漏洞描述**: 详细描述发现的安全问题
2. **影响范围**: 说明漏洞可能造成的影响
3. **复现步骤**: 提供详细的复现方法
4. **建议修复**: 如有修复建议请一并提供

### 🕐 响应时间
- **确认收到**: 24小时内
- **初步评估**: 72小时内
- **修复发布**: 根据严重程度，1-14天内

## 🔐 安全检查清单

### 部署前检查
- [ ] 移除所有硬编码的API密钥
- [ ] 验证.gitignore文件完整性
- [ ] 确认敏感文件不在版本控制中
- [ ] 检查日志文件不包含敏感信息
- [ ] 验证API权限设置最小化

### 使用中检查
- [ ] 定期检查API密钥使用情况
- [ ] 监控异常交易活动
- [ ] 及时更新系统版本
- [ ] 检查系统日志异常

## 🛠️ 安全功能

### 内置安全措施
- **API密钥验证**: 启动时验证API配置
- **权限检查**: 确认API权限充足
- **安全日志**: 记录所有API调用
- **错误处理**: 避免敏感信息泄露

### 推荐安全配置
```python
# config.py 推荐配置
import os
from dotenv import load_dotenv

load_dotenv()

# 从环境变量读取
API_KEY = os.getenv('OKX_API_KEY')
SECRET_KEY = os.getenv('OKX_SECRET_KEY')
PASSPHRASE = os.getenv('OKX_PASSPHRASE')

# 验证配置
if not all([API_KEY, SECRET_KEY, PASSPHRASE]):
    raise ValueError("API配置不完整")
```

## 🔄 安全更新通知

### 通知渠道
- **GitHub Releases**: 重要安全更新
- **Security Advisories**: 安全公告
- **邮件通知**: 订阅安全更新

### 更新策略
- **紧急安全更新**: 立即发布
- **一般安全优化**: 随版本发布
- **安全建议**: 定期发布

## 📖 安全资源

### 相关文档
- [API安全指南](docs/api-security.md)
- [部署安全检查](docs/deployment-security.md)
- [事件响应计划](docs/incident-response.md)

### 安全工具
- [配置验证工具](tools/config-validator.py)
- [安全检查脚本](scripts/security-check.sh)
- [密钥轮换工具](tools/key-rotation.py)

## ⚖️ 法律声明

- 本项目仅供教育和研究目的
- 用户需承担使用风险和法律责任
- 请遵守当地金融法规和交易所政策
- 系统不承担任何投资损失责任

---

**记住：安全是每个人的责任！**

如有任何安全疑问，请随时联系我们。 