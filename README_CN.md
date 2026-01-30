# find-skills（Windows 兼容版）

[English](./README.md)

这是 [vercel-labs/skills find-skills](https://github.com/vercel-labs/skills) 的 Windows 兼容版本，修复了在 Windows 上 Claude Code 中搜索无输出的问题。

## 问题

在 Windows 上，Claude Code 使用的 Bash/Git Bash 环境无法正确处理 `npx skills` 命令——命令执行后没有任何输出。

```bash
# ❌ 在 Windows 的 Claude Code 中没有输出
npx skills find "react"
```

## 解决方案

这个 fork 修改了 SKILL.md，让 Claude Code 使用 PowerShell 来运行 skills 命令：

```bash
# ✅ 在 Windows 上正常工作
powershell -Command "npx skills find 'react'"
```

## 安装方法

### 步骤1：先安装原版 find-skills

```bash
npx skills add vercel-labs/skills@find-skills -g -y
```

### 步骤2：替换为 Windows 版本

1. 打开：https://github.com/KimYx0207/findskill/blob/main/windows/SKILL.md
2. 复制全部内容
3. 替换到这个路径：
   ```
   C:\Users\你的用户名\.agents\skills\find-skills\SKILL.md
   ```

### 步骤3：重启 Claude Code

关闭并重新打开 Claude Code。

### 步骤4：验证安装

对 Claude Code 说："帮我搜索一个数据分析的 skill"

如果看到搜索结果，说明安装成功。

## 文件结构

```
findskill/
├── README.md           # 英文文档
├── README_CN.md        # 中文文档（本文件）
├── LICENSE             # MIT 许可证
├── original/
│   └── SKILL.md        # 原版（来自 vercel-labs）
└── windows/
    └── SKILL.md        # Windows 兼容版
```

## 主要修改

1. **添加 Windows 兼容性警告**
2. **所有命令改为** `powershell -Command "..."` 格式
3. **添加中英文关键词对照**（搜索只支持英文）
4. **添加故障排除章节**

## 使用方法

安装后，对 Claude Code 说：

- "帮我搜索一个 react 的 skill"
- "find a skill for code review"
- "搜索 skill data analysis"

Claude Code 会正确使用 PowerShell 运行搜索。

## 三个大坑

### 坑1：搜索只支持英文

```bash
# ❌ 中文搜索没有结果
npx skills find 数据分析

# ✅ 用英文关键词
npx skills find data analysis
```

### 坑2：触发不稳定

因为 AI 是语义理解的，同样的话有时候触发，有时候不触发。

```
⚠️ "帮我找个做数据分析的工具" → 可能触发，也可能不触发
✅ "帮我搜索一个数据分析的 skill" → 更容易触发
```

**建议**：想稳定触发，话里带上 "skill" 这个词。

### 坑3：Windows 上原版不能用

原版在 Windows 的 Claude Code 中完全不能用，这就是为什么需要这个 fork。

## 中英文关键词对照

| 你想做的事 | 搜索关键词 |
|-----------|-----------|
| 数据分析 | data analysis |
| 做PPT | ppt |
| 代码审查 | code review |
| 部署上线 | deploy |
| 写测试 | testing |
| 做视频 | video |
| React开发 | react |

## 常见问题

**Q：搜索没有结果？**
A：用英文关键词，中文搜索不支持。

**Q：Windows 上没有输出？**
A：用这个 Windows 版本替换原版。

**Q：怎么验证安装成功？**
A：运行 `npx skills list -g`，看到 find-skills 就是成功了。

## 致谢

- 原版：[vercel-labs/skills](https://github.com/vercel-labs/skills)
- Windows 修复：[@KimYx0207](https://github.com/KimYx0207)

## 许可证

MIT（与原版相同）
