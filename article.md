# find-skills 24小时装了15.3K次,这个"帮AI找技能"的技能火了

## 其他标题选项

【标题2】24小时15.3K安装量,find-skills凭什么登顶排行榜第一?
【标题3】AI Agent终于有了"搜索指南",find-skills一天15.3K安装
【标题4】老金试了find-skills才知道,AI Agent能自己找工具了
【标题5】这个技能让AI Agent学会"搜索",24小时爆了15.3K安装

**为什么选择标题1**:
数字型公式,用"24小时"和"15.3K"制造强烈的时间冲击感。
"帮AI找技能的技能"准确描述find-skills的元能力定位。
24小时比一周更有爆发感,符合热点文章特征。
标题简洁(28字),信息密度高,易于理解和传播。
突出核心价值:让AI Agent能自己找工具,降低使用门槛。

---

老金昨天装了个技能,装完之后整个人都傻了。

**为什么?**

因为这个技能不是帮你做具体事情的。
它是一份"说明书",教AI Agent怎么帮你搜索和安装其他技能。

**更绝的是**:
24小时,装了15.3K次。
排行榜第二名才5.8K次,差距2.6倍。

它叫find-skills。
**装上之后,你的AI Agent就知道怎么帮你搜索skills.sh生态里的技能了**。

就像给AI一份"搜索指南"。

## 谁适合用find-skills?

**先说清楚,这个东西不是所有人都需要**。

**适合的人**:
- 正在用Claude Code、Cursor、Windsurf等AI编程工具的开发者
- 想让AI Agent帮你找工具,而不是自己去翻文档的人
- 经常需要安装新技能包的人

**不适合的人**:
- 不用AI编程工具的人(find-skills需要AI Agent来发挥作用)
- 只想用中文交互的人(**搜索只支持英文关键词**)
- 完全不熟悉命令行的人

**如果你不确定自己适不适合,往下看**。

## find-skills到底是什么?

**说人话:它是一份给AI Agent看的"搜索指南"**。

你装了find-skills之后,会发生什么?

1. 你的AI Agent(比如Claude Code)会读取这份指南
2. 当你说"帮我找个做PPT的工具"时,AI Agent会理解你的意思
3. AI Agent会把你的需求翻译成英文关键词(比如"ppt")
4. AI Agent运行搜索命令:`npx skills find ppt`
5. 搜索结果展示给你,你确认后AI Agent帮你安装

**注意**:
- find-skills本身不会"理解"你说的话,理解是AI Agent做的
- find-skills本身不会"翻译"中文,翻译是AI Agent做的
- find-skills只是告诉AI Agent:"嘿,你可以用这个命令帮用户搜索技能"

**这就是为什么它叫"元能力"**——它不是具体的技能,而是教AI怎么找技能。

## ⚠️ 最重要的坑:find-skills不会自动触发!

**这是老金踩过的最大的坑,必须说清楚**。

### 错误示范(不会触发find-skills)

你说:
> "帮我找个做数据分析的工具"

AI Agent会怎么做?
- ❌ 不会调用find-skills搜索
- ❌ 而是直接推荐Pandas、NumPy、Matplotlib这些通用工具

**为什么?**
因为AI Agent觉得你问的是"数据分析用什么工具",不是"帮我搜索skills.sh里的技能"。

### 正确示范(会触发find-skills)

**方式1:明确说要搜索skill**
> "帮我搜索一个数据分析的**skill**"
> "用find-skills搜索数据分析"
> "在skills.sh里找个数据分析的技能"

**方式2:直接用斜杠命令(如果配置了)**
> "/find-skills data analysis"

**方式3:手动运行命令**
```bash
npx skills find data analysis
```

### 触发关键词

根据find-skills的SKILL.md,以下说法会触发搜索:
- "**find a skill for** X"
- "**is there a skill** that can..."
- "**搜索skill**"
- "**找个skill**"
- "how do I do X" (有时候会触发,但不稳定)

**记住**:要让AI知道你是在找**skill**,不是在问一般性问题。

## ⚠️ 安装前必读(重要!)

### 环境要求

**1. Node.js版本**
```
node --version
# 需要 v18 以上
```

**2. Windows用户特别注意**
> ⚠️ **必须用PowerShell或CMD,不能用Git Bash!**
> Git Bash运行skills命令会没有任何输出,看起来像卡住了。

> ⚠️ **Windows上Claude Code的严重问题**
> Claude Code在Windows上使用的是类Git Bash环境,运行`npx skills find`会没有输出!
> 这意味着**find-skills在Windows的Claude Code中基本不可用**。
>
> **临时解决方案**:手动在PowerShell中运行搜索命令:
> ```powershell
> npx skills find "data analysis"
> ```

**3. 网络要求**
- 能访问npm(国内可能需要换源)
- 能访问GitHub

### 重要限制:搜索只支持英文!

**这是最容易踩的坑**:

```bash
# ❌ 错误:中文搜索没有结果
npx skills find 数据分析
# 输出: No skills found for "数据分析"

# ✅ 正确:用英文关键词
npx skills find data analysis
# 输出: 找到6个相关技能
```

**为什么?**
因为skills.sh是国际化的生态,所有技能名称都是英文。

**好消息是**:
如果你在Claude Code里用,AI Agent会自动帮你翻译。
你说"我要做数据分析",AI Agent会自动搜"data analysis"。

## 怎么安装find-skills?

### 第一步:检查环境

打开**PowerShell**(Windows)或**终端**(Mac/Linux):

```bash
node --version
# 应该显示 v18.x.x 或更高
```

### 第二步:安装find-skills

```bash
npx skills add vercel-labs/skills@find-skills -g -y
```

参数说明:
- `-g` 全局安装(推荐,这样所有项目都能用)
- `-y` 跳过确认提示

### 第三步:验证安装成功

```bash
npx skills list -g
```

应该看到:
```
Global Skills

find-skills ~/.agents/skills/find-skills
  Agents: Antigravity, Claude Code, Codex, Cursor, Gemini CLI +3 more
```

### 第四步:测试搜索功能

```bash
npx skills find react
```

应该看到一堆React相关的技能:
```
Install with npx skills add <owner/repo@skill>

vercel-labs/agent-skills@vercel-react-best-practices
└ https://skills.sh/vercel-labs/agent-skills/vercel-react-best-practices

vercel-labs/agent-skills@vercel-react-native-skills
└ https://skills.sh/vercel-labs/agent-skills/vercel-react-native-skills
...
```

**如果到这一步都正常,恭喜你,安装成功了!**

## find-skills怎么工作?

### 场景A:在AI Agent中使用(推荐)

这是最省心的方式。

**你说**:"帮我找个做数据分析的工具"

**AI Agent会**:
1. 理解你要做数据分析
2. 翻译成英文关键词"data analysis"
3. 运行`npx skills find data analysis`
4. 展示搜索结果给你
5. 问你要不要安装
6. 你确认后,运行安装命令

**你需要做的**:说一句话,然后确认安装。

### 场景B:手动使用CLI

如果你想自己搜索,也可以直接用命令行。

**步骤1:想好英文关键词**

| 你想做的事 | 搜索关键词 |
|-----------|-----------|
| 数据分析 | data analysis |
| 做PPT | ppt, presentation |
| 写代码审查 | code review |
| 部署上线 | deploy, deployment |
| 写测试 | testing |
| 做视频 | video, remotion |

**步骤2:运行搜索命令**

```bash
npx skills find [关键词]
```

**步骤3:查看结果,选择要安装的**

```bash
npx skills add [owner/repo@skill] -g -y
```

## 实战案例(真实可复现)

### 案例1:数据分析

**需求**:我要做数据分析

**搜索命令**:
```bash
npx skills find data analysis
```

**实际结果**:
```
davila7/claude-code-templates@exploratory-data-analysis
└ https://skills.sh/davila7/claude-code-templates/exploratory-data-analysis

ailabs-393/ai-labs-claude-skills@data-analyst
└ https://skills.sh/ailabs-393/ai-labs-claude-skills/data-analyst

pluginagentmarketplace/custom-plugin-python@pandas-data-analysis
└ https://skills.sh/pluginagentmarketplace/custom-plugin-python/pandas-data-analysis
```

**安装命令**:
```bash
npx skills add davila7/claude-code-templates@exploratory-data-analysis -g -y
```

### 案例2:做PPT

**需求**:帮我做个PPT

**搜索命令**:
```bash
npx skills find ppt
```

**实际结果**:
```
anthropics/skills@pptx
└ https://skills.sh/anthropics/skills/pptx

daymade/claude-code-skills@ppt-creator
└ https://skills.sh/daymade/claude-code-skills/ppt-creator

jwynia/agent-skills@pptx-generator
└ https://skills.sh/jwynia/agent-skills/pptx-generator
```

**安装命令**:
```bash
npx skills add anthropics/skills@pptx -g -y
```

### 案例3:代码审查

**需求**:帮我审查代码

**搜索命令**:
```bash
npx skills find code review
```

**实际结果**:
```
google-gemini/gemini-cli@code-reviewer
└ https://skills.sh/google-gemini/gemini-cli/code-reviewer

wshobson/agents@code-review-excellence
└ https://skills.sh/wshobson/agents/code-review-excellence

skillcreatorai/ai-agent-skills@code-review
└ https://skills.sh/skillcreatorai/ai-agent-skills/code-review
```

**安装命令**:
```bash
npx skills add google-gemini/gemini-cli@code-reviewer -g -y
```

## 搜索关键词速查表

**这是老金整理的中英文对照表,建议收藏**:

| 你想做的事 | 搜索关键词 | 推荐技能 |
|-----------|-----------|----------|
| 数据分析 | data analysis | exploratory-data-analysis |
| 做PPT | ppt, presentation | pptx |
| 写文章 | writing | writing-skills |
| 代码审查 | code review | code-reviewer |
| 部署上线 | deploy | vercel-deployment |
| 写测试 | testing | webapp-testing |
| 做视频 | video, remotion | remotion-best-practices |
| React开发 | react | vercel-react-best-practices |
| Python开发 | python | python-testing-patterns |
| 前端设计 | frontend, design | frontend-design |

**搜索技巧**:
1. 用具体关键词:"react testing"比"testing"效果好
2. 试试同义词:如果"deploy"没找到,试试"deployment"
3. 用英文:中文搜索没有结果

## 常见问题FAQ

### Q0:我说"帮我找个工具",AI没有调用find-skills?

**这是最常见的问题!**

AI Agent不会自动触发find-skills,你需要明确说要搜索**skill**:

```
❌ "帮我找个做数据分析的工具"  → AI直接推荐Pandas、NumPy
✅ "帮我搜索一个数据分析的skill" → AI调用find-skills搜索
✅ "用find-skills搜索data analysis" → AI调用find-skills搜索
```

**关键词**:skill、搜索skill、find-skills、skills.sh

### Q1:为什么搜索没有结果?

**可能的原因**:
1. 用了中文关键词 → 改用英文
2. 关键词太具体 → 试试更通用的词
3. 网络问题 → 检查能否访问npm

### Q2:Windows上Claude Code搜索没有输出?

**这是Windows特有的严重问题!**

Claude Code在Windows上使用的Bash环境运行`npx skills find`会没有任何输出。

**临时解决方案**:
1. 打开一个单独的PowerShell窗口
2. 手动运行搜索命令:
```powershell
npx skills find "data analysis"
```
3. 看到结果后,复制安装命令回Claude Code执行

**或者让Claude Code用PowerShell运行**:
```bash
powershell -Command "npx skills find 'data analysis'"
```

### Q3:Windows上命令没反应?

**解决方案**:
1. 不要用Git Bash,改用PowerShell或CMD
2. 检查Node.js是否安装正确:`node --version`

### Q3:安装后怎么使用?

**在Claude Code中**:
1. 重启Claude Code(让它读取新安装的skill)
2. 直接说你要做什么,比如"帮我做个PPT"
3. AI会自动调用已安装的skill

### Q4:怎么知道skill安装成功了?

```bash
npx skills list -g
```

会列出所有已安装的全局skills。

### Q5:skill和MCP有什么区别?

**简单说**:
- **Skill**:知识/指南,教AI怎么做事(比如React最佳实践)
- **MCP**:工具/能力,让AI能做新的事(比如读取文件、调用API)

Skill是"知道怎么做",MCP是"能够做"。

### Q6:怎么卸载skill?

```bash
npx skills remove [skill名称] -g
```

### Q7:怎么更新skill?

```bash
npx skills update
```

## 为什么find-skills这么火?

24小时15.3K安装量,2天前才发布,为什么这么火?

老金觉得有三个原因:

**原因1:解决根本问题**
Skills生态有几百个技能包,但你怎么知道该装哪个?
find-skills解决的就是"技能发现"这个根本问题。

**原因2:降低使用门槛**
以前你得手动翻文档、记名字、复制命令。
现在AI Agent读了find-skills的指南后,就知道怎么帮你搜索了。

**原因3:24小时排行榜数据**
find-skills在24小时排行榜上登顶第一:
- 第1名: find-skills (15.3K)
- 第2名: vercel-react-best-practices (5.8K)
- 第3名: remotion-best-practices (5.0K)
- 第4名: web-design-guidelines (4.4K)
- 第5名: frontend-design (3.0K)

**第一名是第二名的2.6倍**,这说明find-skills的需求有多强烈。

## 老金的建议

如果你在用AI Agent(Claude Code、Cursor等),建议装上find-skills。

**三个理由**:

**理由1:省时间**
不用自己去翻文档找技能,告诉AI你要做什么就行。

**理由2:AI帮你翻译**
你说中文,AI Agent会自动翻译成英文关键词去搜索。

**理由3:一站式体验**
从搜索到安装,都在AI Agent里完成,不用切换窗口。

**安装命令**:
```bash
npx skills add vercel-labs/skills@find-skills -g -y
```

**验证安装**:
```bash
npx skills list -g
```

## 最后说两句

老金看得出来,find-skills这个东西有点意思。

它不是又一个具体的技能,而是一份"搜索指南"。
装上之后,AI Agent就知道怎么帮你找工具了。

**这是元能力**。

24小时15.3K的安装量,是第二名的2.6倍,说明开发者已经认可了这个价值。

如果你还在手动翻文档找技能,试试find-skills吧。
装上之后,你会发现AI Agent突然变聪明了。

不是它变聪明了,是它终于知道去哪找工具了。

**但记住**:
- 搜索只支持英文关键词
- Windows用户要用PowerShell
- 需要AI Agent来发挥作用

---

**参考来源**:
- find-skills官方文档: https://skills.sh/vercel-labs/skills/find-skills
- Skills CLI文档: https://skills.sh/docs
- Vercel Skills GitHub仓库: https://github.com/vercel-labs/skills
- Skills v1.1.1更新日志: https://vercel.com/changelog/skills-v1-1-1-interactive-discovery-open-source-release-and-agent-support
- Introducing skills生态系统: https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem
