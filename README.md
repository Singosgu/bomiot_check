# MAC Validator

一个用于 MAC 地址验证和加密的 Python 包。

## 功能特点

- 获取系统 MAC 地址
- MAC 地址加密（支持自定义有效期）
- MAC 地址验证
- 跨平台支持（Windows、macOS、Linux）
- 支持 Python 3.9 及以上版本

## 安装

```bash
pip install mac-validator
```

## 使用示例

```python
from mac_validator import (
    get_mac_address_py,
    encrypt_info,
    encrypt_info_custom,
    verify_info,
    verify_info_custom
)

# 获取MAC地址
mac = get_mac_address_py()
print(f"本机MAC地址: {mac}")

# 加密MAC地址（7天有效期）
encrypted = encrypt_info()
print(f"加密信息: {encrypted}")

# 验证加密信息
mac_mismatch, expired = verify_info(encrypted)
print(f"MAC地址是否不匹配: {mac_mismatch}")
print(f"是否已过期: {expired}")

# 自定义MAC地址和有效期
custom_mac = "[00, 11, 22, 33, 44, 55]"
days = 30
encrypted_custom = encrypt_info_custom(custom_mac, days)
mac_mismatch, expired = verify_info_custom(encrypted_custom, custom_mac)
```

## 开发

### 环境要求

- Python 3.9+
- Rust
- maturin
- cibuildwheel

### 构建

```bash
# 安装依赖
pip install maturin cibuildwheel

# 构建
maturin build
```

## 许可证

MIT License 