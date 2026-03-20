---
name: "code-translator"
description: "代码翻译工具，支持代码注释翻译、文档翻译和API集成。当用户需要翻译代码注释、技术文档或集成翻译功能时调用。"
---

# Code Translator - 智能代码翻译助手

## 技能概述

这是一个专门为开发者设计的代码翻译工具，集成多种翻译引擎和VSCode扩展功能，帮助您高效处理代码注释和技术文档的翻译需求。

## 触发条件

当用户说以下任意一句话时自动触发：
- "翻译这段代码注释"
- "帮我翻译技术文档"
- "集成翻译功能"
- "代码注释翻译"
- "文档翻译"

## 核心功能

### 1. 多引擎翻译服务
**支持的翻译引擎**：
- **DeepSeek API** - 智能AI翻译，理解代码上下文
- **百度翻译API** - 专业翻译服务，准确度高
- **Google翻译API** - 多语言支持，响应快速

**智能选择策略**：
- 按优先级自动尝试多个引擎
- 失败自动切换到备用引擎
- 支持批量翻译和实时翻译

### 2. VSCode扩展集成
**快捷键配置**：
- `Ctrl+Shift+T` - 翻译选中注释
- `Ctrl+Shift+F` - 翻译文件所有注释

**功能特性**：
- 实时翻译代码注释
- 批量处理文件注释
- 翻译结果面板显示
- 支持多种编程语言

### 3. 自定义翻译脚本
**脚本功能**：
- 代码注释自动提取
- 多文件批量翻译
- 翻译结果导出
- 自定义翻译规则

## 使用场景

### 场景一：代码注释翻译
```
用户：翻译这段注释
原文：// This function handles user authentication
Skill：这个函数处理用户认证
```

### 场景二：技术文档翻译
```
用户：帮我翻译这个API文档
原文：The API provides endpoints for user management
Skill：该API提供用户管理的端点
```

### 场景三：批量翻译
```
用户：翻译这个文件的所有注释
Skill：正在提取注释...
      找到15条注释
      开始批量翻译...
      翻译完成，已生成翻译报告
```

## 安装和配置

### 1. API密钥配置
```bash
# 设置环境变量
export BAIDU_APP_ID=your_app_id
export BAIDU_APP_KEY=your_app_key
export GOOGLE_API_KEY=your_google_key
```

### 2. VSCode扩展安装
```bash
# 安装语言包
code --install-extension ms-ceintl.vscode-language-pack-zh-hans

# 安装注释翻译扩展
code --install-extension intellsmi.comment-translate
```

### 3. 自定义配置
创建配置文件 `~/.code-translator/config.json`：
```json
{
  "preferred_engine": "deepseek",
  "auto_translate": true,
  "target_language": "zh",
  "keybindings": {
    "translate_selection": "ctrl+shift+t",
    "translate_file": "ctrl+shift+f"
  }
}
```

## 使用示例

### 示例一：单条翻译
```python
from translator_api import MultiTranslator

translator = MultiTranslator()
text = "This is a sample comment for translation"
result = translator.smart_translate(text, 'zh')
print(result)  # 这是一个用于翻译的示例注释
```

### 示例二：批量翻译
```python
from vscode_translator import CodeTranslator

translator = CodeTranslator()
file_path = "/path/to/your/file.py"
results = translator.translate_file_comments(file_path)

for key, value in results.items():
    print(f"原文: {value['original']}")
    print(f"译文: {value['translated']}")
    print("-" * 40)
```

### 示例三：VSCode集成
1. 打开VSCode
2. 选中要翻译的注释
3. 按 `Ctrl+Shift+T`
4. 查看翻译结果

## 技术特性

### 1. 智能注释提取
- 支持多种注释风格（#、//、/* */）
- 自动识别编程语言
- 处理多行注释

### 2. 翻译质量优化
- 代码术语专业翻译
- 保持技术准确性
- 上下文理解

### 3. 性能优化
- 请求失败自动重试
- 批量处理优化
- 缓存机制

## 故障排除

### 常见问题
1. **API密钥错误**：检查环境变量设置
2. **网络连接问题**：检查网络连接和代理设置
3. **VSCode扩展不工作**：重启VSCode或重新安装扩展

### 调试模式
启用调试模式查看详细日志：
```python
import os
os.environ['DEBUG'] = 'true'
```

这个Skill将帮助您高效处理代码翻译需求，提升开发效率！