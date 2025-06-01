# 数字签名验证指南

本指南说明如何验证《数字（0）革命宣言》报告的数字签名，确保内容真实性和完整性。

## 为什么需要数字签名？

在数字时代，确保文档真实性和完整性至关重要。数字签名提供了一种密码学方法，用于：

1. **验证作者身份**：确保文档确实由声称的作者创建
2. **确保内容完整性**：验证文档自签名后未被修改
3. **防止伪造**：阻止未经授权的伪造或更改

这与报告中讨论的"零验证信任体系"理念高度一致，展示了如何在实践中应用这些理念。

## 验证步骤

### 准备工作

您需要安装GnuPG (GPG)，这是一个免费的加密软件：

- **Windows**: 下载并安装 [Gpg4win](https://www.gpg4win.org/)
- **macOS**: 通过Homebrew安装: `brew install gnupg`
- **Linux**: 大多数发行版已预装，或使用包管理器安装: `sudo apt install gnupg` 或 `sudo dnf install gnupg`

### 验证过程

1. **导入作者公钥**

   ```bash
   gpg --import public_key.asc
   ```

2. **验证签名**

   ```bash
   gpg --verify signature.asc digital_zero_revolution_full.md
   ```

3. **检查验证结果**

   成功验证将显示类似以下信息：

   ```
   gpg: Good signature from "Digital Zero Revolution <contact@digitalzero.org>" [ultimate]
   ```

   如果看到警告"This key is not certified with a trusted signature"，这是正常的，表示您尚未通过Web of Trust验证该密钥。

   如果内容被修改，将显示错误信息：

   ```
   gpg: BAD signature from "Digital Zero Revolution <contact@digitalzero.org>" [ultimate]
   ```

## 密钥指纹验证

为增加安全性，您应该验证公钥的指纹：

```bash
gpg --fingerprint contact@digitalzero.org
```

正确的指纹应为：
```
8A31 F57C 6E09 8D54 8F37  E903 6D0B 8B72 3D25 9F61
```

## 高级验证方法

对于需要更高安全性的用户，可通过多种渠道交叉验证密钥指纹：

1. 项目官方网站
2. 社交媒体账号
3. 可信的密钥服务器
4. 参与者线下会议

## 问题排解

如遇验证问题，请检查：

1. 公钥已正确导入
2. 文件路径正确
3. 签名和原文件未被修改
4. GPG版本兼容性

## 联系方式

如有任何与验证相关的问题，请通过GitHub Issues联系我们。