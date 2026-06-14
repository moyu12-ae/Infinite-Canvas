# PR: 添加 macOS 应用打包支持

## 📋 变更说明

本 PR 为 Infinite Canvas 添加了 macOS 应用打包功能，用户可以直接下载 `.app` 或 `.dmg` 安装包，无需手动配置 Python 环境。

## ✨ 新增功能

### 1. 本地打包脚本 (`build_mac.sh`)
- 一键打包为 macOS `.app` 应用
- 自动安装依赖和 PyInstaller
- 支持生成 DMG 安装包
- 用户可自行构建，无需等待 Release

### 2. GitHub Actions 自动构建 (`.github/workflows/build-mac.yml`)
- 自动构建 Intel 和 Apple Silicon 两种架构
- 创建 Release 时自动上传 DMG 安装包
- 支持手动触发构建（workflow_dispatch）
- 构建产物保留 30 天

## 📦 支持的架构

| 架构 | 说明 |
|------|------|
| `x86_64` | Intel Mac |
| `arm64` | Apple Silicon (M1/M2/M3) |

## 🚀 使用方式

### 方式一：下载 Release 安装包（推荐）
1. 前往 [Releases](https://github.com/hero8152/Infinite-Canvas/releases) 页面
2. 下载对应架构的 `.dmg` 文件
3. 双击安装，拖动到 Applications 文件夹

### 方式二：本地构建
```bash
# 克隆仓库
git clone https://github.com/hero8152/Infinite-Canvas.git
cd Infinite-Canvas

# 运行打包脚本
chmod +x build_mac.sh
./build_mac.sh

# 构建完成后，应用位于 dist/Infinite Canvas/Infinite Canvas.app
```

## 📝 注意事项

1. **图标文件**：当前使用项目中的 `static/images/logo.png` 作为应用图标。如需更专业的图标，建议创建 `.icns` 格式文件并放置在 `static/images/icon.icns`。

2. **首次运行**：macOS 可能会提示"无法验证开发者"，用户需要：
   - 右键点击应用 → 选择"打开"
   - 或前往 系统设置 → 隐私与安全性 → 安全性 → 点击"仍要打开"

3. **代码签名**：当前未包含代码签名。如需发布到 App Store 或消除安全警告，需要 Apple Developer 账号进行签名。

## 🧪 测试

- [ ] 在 Intel Mac 上测试构建和运行
- [ ] 在 Apple Silicon Mac 上测试构建和运行
- [ ] 验证所有功能正常（API 调用、ComfyUI 连接等）
- [ ] 测试 DMG 安装流程

## 📸 截图

（可选：添加应用运行截图）

## 🔗 相关 Issue

（如有相关 Issue，请在此引用）

---

**感谢审阅！如有任何问题或建议，请随时反馈。** 🙏
