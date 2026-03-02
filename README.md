# 魔法指南

一站式代理工具配置指南集合

## 简介

本项目汇集了多平台代理工具的详细使用教程，涵盖 Windows、macOS、Linux、iOS、Android 及鸿蒙系统，帮助用户快速上手各类代理工具。

### 🔗 魔法链接

| 名称 | 地址 |
|------|------|
| CloudFisher | https://cloudfisher.one |
| StarTrail | https://qiyuanya.com |

---

## 为什么需要代理工具？

### 常见使用场景

| 场景 | 说明 |
|------|------|
| 🔧 开发工作 | 访问 GitHub、Docker Hub、NPM 等技术资源 |
| 📚 学术研究 | 查阅国际学术论文、技术文档 |
| 💼 跨境业务 | 外贸电商、跨国企业办公协作 |
| ☁️ 云服务 | 访问 AWS、Google Cloud、Azure 等国际云平台 |
| 🔒 网络安全 | 渗透测试、安全审计、隐私保护 |

### 工作原理

```
传统访问方式：
+--------+          +------------+          +-------------+
|  你的  |  ──────> |  网络障碍  |  ╳ ╳ ╳  |  目标服务器  |
|  设备  |          |            |          |             |
+--------+          +------------+          +-------------+

使用代理工具：
+--------+      +-----------+      +-------------+
|  你的  | ---> | 代理服务器 | ---> |  目标服务器  |
|  设备  |      | (中转节点) |      |             |
+--------+      +-----------+      +-------------+
     ↓                                    ↓
  加密传输                          正常响应
```

**代理工具的作用：**
1. **中转访问**：通过代理服务器中转网络请求
2. **加密传输**：保护数据传输安全
3. **智能分流**：规则模式下自动选择直连或代理
4. **隐私保护**：隐藏真实 IP 地址

---

## 内容

- **ClashVerge 指南** - Windows/macOS/Linux 电脑端代理工具教程
- **Mihomo 指南** - Linux 服务器代理配置教程
- **手机使用指南** - iOS/Android/鸿蒙移动端代理工具教程

## 快速开始

请先阅读 [使用必看.md](使用必看.md)

---

## Markdown 新手指南

### 什么是 Markdown？

Markdown 是一种轻量级标记语言，使用简单的符号来格式化文本。它的设计目标是让文档易读易写。

**优势：**
- 📝 纯文本格式，兼容性强
- 🎯 语法简单，几分钟即可上手
- 📱 可在任何平台查看和编辑
- 🔗 GitHub、GitLab 等平台原生支持

### 如何查看 Markdown 文件？

#### 在线查看（最简单）
1. **GitHub 网页**：直接在 GitHub 仓库中点击 `.md` 文件即可查看渲染后的效果
2. **在线编辑器**：
   - [StackEdit](https://stackedit.io/)
   - [Dillinger](https://dillinger.io/)

#### 本地查看
| 平台 | 推荐工具 | 说明 |
|------|---------|------|
| Windows | Typora、MarkText、Obsidian | 所见即所得编辑器 |
| macOS | Typora、MacDown、Obsidian | 原生支持体验好 |
| Linux | Typora、MarkText、Obsidian | 开源免费选择多 |
| 通用 | VS Code + Markdown插件 | 程序员首选 |

### 基础语法速查

```markdown
# 一级标题
## 二级标题
### 三级标题

**粗体文字**
*斜体文字*
~~删除线~~

- 无序列表项 1
- 无序列表项 2

1. 有序列表项 1
2. 有序列表项 2

[链接文字](https://example.com)
![图片描述](图片路径)

`行内代码`

​```代码块
多行代码
​```

> 引用文字

---

表格 | 说明
-----|-----
内容1 | 说明1
内容2 | 说明2
```

### 学习资源

- [Markdown 官方教程](https://www.markdownguide.org/)
- [Markdown 语法说明（中文）](https://www.runoob.com/markdown/md-tutorial.html)
- [GitHub Flavored Markdown](https://docs.github.com/cn/get-started/writing-on-github)

---

## 许可证

本项目仅供学习交流使用
