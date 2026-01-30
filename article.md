# find-skills 24小时装了15.3K次,这个"帮AI找技能"的技能火了

## 其他标题选项

【标题2】24小时15.3K安装量,find-skills凭什么登顶排行榜第一?
【标题3】AI Agent终于有了"搜索指南",find-skills一天15.3K安装
【标题4】老金试了find-skills才知道,AI Agent能自己找工具了
【标题5】这个技能让AI Agent学会"搜索",24小时爆了15.3K安装

**为什么选择标题1**:
数字型公式,用"24小时"和"15.3K"制造强烈的时间冲击感。
"帮AI找技能的技能"准确描述find-skills的元能力定位。

---

老金昨天装了个技能,装完之后整个人都傻了。

**为什么?**

因为这个技能不是帮你做具体事情的。
它是一份"说明书",教AI Agent怎么帮你搜索和安装其他技能。

**更绝的是**:
24小时,装了15.3K次。
排行榜第二名才5.8K次,差距2.6倍。

它叫find-skills。

## find-skills是什么?

**一句话:给AI Agent的"搜索指南"**。

装上之后,你说"帮我搜索一个数据分析的skill",AI Agent就会:
1. 翻译成英文关键词"data analysis"
2. 运行`npx skills find data analysis`
3. 展示搜索结果
4. 帮你安装

**这是元能力**——不是具体技能,而是教AI怎么找技能。

## 原版的问题

官方版本来自Vercel:
```bash
npx skills add vercel-labs/skills@find-skills -g -y
```

**但是有三个大坑**:

| 坑 | 问题 | 后果 |
|----|------|------|
| **坑1** | 搜索只支持英文 | 中文搜索返回空 |
| **坑2** | 说"找工具"不触发 | 要明确说"搜索skill" |
| **坑3** | **Windows上完全不能用** | Claude Code的Bash环境运行npx skills没有输出 |

**坑3最致命**——Windows用户装了原版,在Claude Code里根本搜不到任何东西。

## Windows用户直接装这个

老金fork了一份,修复了Windows兼容性问题:

**GitHub**: https://github.com/KimYx0207/findskill

### 安装方法

**方法1:替换本地文件(推荐)**

1. 先装原版:
```bash
npx skills add vercel-labs/skills@find-skills -g -y
```

2. 下载Windows版SKILL.md:
```
https://github.com/KimYx0207/findskill/blob/main/windows/SKILL.md
```

3. 替换本地文件:
```
C:\Users\你的用户名\.agents\skills\find-skills\SKILL.md
```

4. 重启Claude Code

**方法2:手动复制内容**

1. 打开 https://github.com/KimYx0207/findskill/blob/main/windows/SKILL.md
2. 复制全部内容
3. 粘贴到 `C:\Users\你的用户名\.agents\skills\find-skills\SKILL.md`
4. 重启Claude Code

### 验证安装

重启Claude Code后,说:
> "帮我搜索一个数据分析的skill"

如果看到搜索结果,说明安装成功。

## 使用方法

### 触发方式

```
❌ "帮我找个做数据分析的工具"  → 不会触发,AI直接推荐Pandas
✅ "帮我搜索一个数据分析的skill" → 触发find-skills搜索
✅ "用find-skills搜索data analysis" → 触发find-skills搜索
```

**关键词**:必须包含"skill"、"搜索skill"、"find-skills"

### 中英文关键词对照

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

**Q: 搜索没有结果?**
A: 用英文关键词,中文搜索不支持。

**Q: Windows上没有输出?**
A: 用我的Windows版本,或者手动在PowerShell里运行:
```powershell
npx skills find "data analysis"
```

**Q: 怎么验证安装成功?**
A: 运行 `npx skills list -g`,看到find-skills就是成功了。

## 最后

find-skills是个好东西,但原版在Windows上有严重问题。

**Windows用户直接用我的版本**: https://github.com/KimYx0207/findskill

装上之后,你的AI Agent就能帮你搜索skills.sh生态里的几百个技能了。

---

**参考来源**:
- find-skills官方: https://skills.sh/vercel-labs/skills/find-skills
- Windows兼容版: https://github.com/KimYx0207/findskill
- Skills CLI文档: https://skills.sh/docs
