# 事实核验 - iOS Shortcuts

一个用于快速核验信息真实性的iOS快捷指令，支持X/Twitter内容提取和Gemini AI分析。

## 功能特点

- 🐦 **X/Twitter智能处理**：自动识别X/Twitter链接，通过API获取完整推文内容
- 🤖 **Gemini AI分析**：使用Google Gemini进行事实核查
- 📋 **一键分享**：从任意App分享内容即可触发核验
- 🔗 **无需API密钥**：直接使用Gemini App，无需注册API

## 工作流程

```
分享内容 → 判断URL类型
  ├─ X/Twitter URL → FxTwitter API获取内容 → Gemini分析
  └─ 其他内容 → 直接传给Gemini分析
```

## 安装方法

### 方法一：直接导入（推荐）

1. 下载 `事实核验.shortcut` 文件
2. 在iPhone/iPad上打开文件
3. 系统会自动打开"快捷指令"App并提示添加
4. 点击"添加快捷指令"

### 方法二：手动创建

参考 [shortcuts-x-twitter-only.md](./shortcuts-x-twitter-only.md) 中的详细步骤。

## 使用方法

1. 在任意App中选中要核验的内容
2. 点击"分享" → 选择"事实核验"
3. 快捷指令会自动：
   - 如果是X/Twitter链接：提取推文内容
   - 其他内容：直接传递给Gemini
4. 自动打开Gemini App
5. 粘贴并获取核验结果

## 技术细节

### X/Twitter内容提取

使用 [FxTwitter API](https://github.com/FxTwitter/FxTwitter)：
- API端点：`https://api.fxtwitter.com/[tweet_url]`
- 无需认证，完全免费
- 返回JSON格式的推文内容

### Prompt模板

快捷指令会自动附加以下prompt（可根据需要修改）：

```
请以表格形式核验以下内容的真实性：
| 总结 | 事实 | 验证 |
|------|------|------|
| [内容总结] | [关键事实] | [验证结果] |
```

## 文件说明

- `事实核验.shortcut` - 快捷指令文件（可直接导入）
- `shortcuts-x-twitter-only.md` - 详细配置教程
- `x-twitter-solution.md` - X/Twitter解决方案说明
- `research-findings.md` - 相关研究笔记

## 自定义

你可以根据需要修改快捷指令：

1. **修改Prompt**：在快捷指令编辑界面修改"文本"操作中的prompt
2. **添加更多平台**：参考X/Twitter的处理方式，添加其他平台的特殊处理
3. **更换AI工具**：可以将Gemini替换为其他AI App

## 系统要求

- iOS 16.0 或更高版本
- 已安装 Google Gemini App

## 许可证

MIT License - 自由使用和修改

## 贡献

欢迎提交Issue和Pull Request！

## 致谢

- [FxTwitter](https://github.com/FxTwitter/FxTwitter) - Twitter内容提取API
- Google Gemini - AI分析引擎
