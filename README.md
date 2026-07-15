[English](./README.md) | [中文](./README_CN.md)

# find-skills (Windows Compatible Fork)

<div align="center">

![GitHub stars](https://img.shields.io/github/stars/KimYx0207/findskill?style=social)
![GitHub forks](https://img.shields.io/github/forks/KimYx0207/findskill?style=social)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

**Windows 兼容版 Claude Code 技能搜索工具**

</div>

> This repository has been merged into [Kim Service](https://github.com/KimYx0207/Kim_Service) and no longer publishes standalone releases. Please use Kim Service for new versions, installation instructions, and release notes.

> 🔗 **GitHub仓库**：[https://github.com/KimYx0207/findskill](https://github.com/KimYx0207/findskill)

> 老金的开源知识库，实时更新群二维码：https://my.feishu.cn/wiki/OhQ8wqntFihcI1kWVDlcNdpznFf

---

## 📞 联系方式

<div align="center">
  <img src="https://raw.githubusercontent.com/KimYx0207/Claude-Code-x-OpenClaw-Guide-Zh/main/images/二维码基础款.png" alt="联系方式" width="600"/>
  <p><strong>获取更多AI资讯和技术支持</strong></p>
  <p>
    🌐 <a href="https://www.aiking.dev/">aiking.dev</a>
  </p>
</div>

---

[中文文档](./README_CN.md)

A Windows-compatible fork of [vercel-labs/skills find-skills](https://github.com/vercel-labs/skills) that fixes the empty output issue in Claude Code on Windows.

## The Problem

On Windows, Claude Code uses a Bash/Git Bash environment that doesn't properly handle `npx skills` commands - they return empty output silently.

```bash
# ❌ This returns nothing on Windows in Claude Code
npx skills find "react"
```

## The Solution

This fork modifies the SKILL.md to instruct Claude Code to use PowerShell for running skills commands:

```bash
# ✅ This works on Windows
powershell -Command "npx skills find 'react'"
```

## Installation

### Step 1: Install the original find-skills

```bash
npx skills add vercel-labs/skills@find-skills -g -y
```

### Step 2: Replace with Windows version

1. Open: https://github.com/KimYx0207/findskill/blob/main/windows/SKILL.md
2. Copy all content
3. Replace the file at:
   ```
   C:\Users\<YourUsername>\.agents\skills\find-skills\SKILL.md
   ```

### Step 3: Restart Claude Code

Close and reopen Claude Code.

### Step 4: Verify

Say to Claude Code: "find a skill for data analysis"

If you see search results, installation is successful.

## Files

```
findskill/
├── README.md           # English documentation (this file)
├── README_CN.md        # Chinese documentation
├── LICENSE             # MIT License
├── original/
│   └── SKILL.md        # Original version from vercel-labs
└── windows/
    └── SKILL.md        # Windows-compatible version
```

## Key Changes

1. **Added Windows compatibility warning** at the top
2. **Changed all commands** to use `powershell -Command "..."` format
3. **Added Chinese to English keyword reference** (search only supports English)
4. **Added troubleshooting section**

## Usage

After installation, ask Claude Code:

- "find a skill for react"
- "is there a skill for code review"
- "search skill for data analysis"

Claude Code will now correctly use PowerShell to run the search.

## Known Limitations

1. **Search only supports English keywords** - Chinese queries need to be translated by AI
2. **Trigger is semantic** - AI may or may not trigger find-skills depending on how you phrase it. Adding "skill" to your request makes it more reliable.
3. **Windows only** - macOS/Linux users should use the original version

## Credits

- Original skill: [vercel-labs/skills](https://github.com/vercel-labs/skills)
- Windows fix: [@KimYx0207](https://github.com/KimYx0207)

## License

MIT (same as original)
