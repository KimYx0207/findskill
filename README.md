# find-skills (Windows Compatible Fork)

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

### Option 1: Replace your existing find-skills (Recommended)

1. Locate your find-skills installation:
   ```
   C:\Users\<YourUsername>\.agents\skills\find-skills\SKILL.md
   ```

2. Replace the content with the Windows version from `windows/SKILL.md`

3. Restart Claude Code

### Option 2: Install as a new skill

```bash
npx skills add KimYx0207/findskill@windows -g -y
```

## Files

```
findskill/
├── README.md           # This file
├── original/
│   └── SKILL.md        # Original version from vercel-labs
└── windows/
    └── SKILL.md        # Windows-compatible version
```

## Key Changes in Windows Version

1. **Added Windows compatibility warning** at the top of the file
2. **Changed all command examples** to use `powershell -Command "..."` format
3. **Added Chinese to English keyword reference** (search only supports English)
4. **Added troubleshooting section**

## Usage

After installation, you can ask Claude Code:

- "帮我搜索一个数据分析的skill" (Find a data analysis skill)
- "find a skill for react"
- "is there a skill for code review"

Claude Code will now correctly use PowerShell to run the search.

## Known Limitations

1. **Search only supports English keywords** - Chinese queries need to be translated
2. **Requires PowerShell** - Won't work in pure Git Bash environment
3. **Windows only** - macOS/Linux users should use the original version

## Credits

- Original skill: [vercel-labs/skills](https://github.com/vercel-labs/skills)
- Windows fix: [@KimYx0207](https://github.com/KimYx0207)

## License

MIT (same as original)
