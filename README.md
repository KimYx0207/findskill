# find-skills (Windows Compatible Fork)

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
