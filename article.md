# 老金用Claude Code半年才发现，原来还有个技能包管理器

## 其他标题选项

【标题2】烦透了手动找技能包？手把手教你用find-skills一键搜索
【标题3】24小时15.3K安装量，find-skills凭什么登顶Skills排行榜第一
【标题4】Claude Code找技能包还在翻文档？这招让你5秒搞定
【标题5】Claude Code官方这波免费，技能包搜索神器老金教你装

**为什么选择标题1**：
"老金用Claude Code半年"制造真实感和时间沉淀，"才发现"制造惊喜感，暗示这是隐藏功能。"技能包管理器"准确描述工具定位，新手能懂。38字在最优区间，品牌词+神器词齐全。

---

老金昨天装了个技能，装完之后整个人都傻了。

**为什么？**

因为这个技能不是帮你做具体事情的。
它是一份"说明书"，教AI Agent怎么帮你搜索和安装其他技能。

**更绝的是**：
24小时，装了15.3K次。
排行榜第二名才5.8K次，差距2.6倍。

它叫find-skills。

## find-skills是什么

**一句话：给AI Agent的"搜索指南"**。

你装了find-skills之后，会发生什么？

1、你的AI Agent（比如Claude Code）会读取这份指南
2、当你说"帮我搜索一个做PPT的skill"时，AI Agent会理解你的意思
3、AI Agent会把你的需求翻译成英文关键词（比如"ppt"）
4、AI Agent运行搜索命令：`npx skills find ppt`
5、搜索结果展示给你，你确认后AI Agent帮你安装

**注意**：
find-skills本身不会"理解"你说的话，理解是AI Agent做的。
find-skills本身不会"翻译"中文，翻译是AI Agent做的。
find-skills只是告诉AI Agent："嘿，你可以用这个命令帮用户搜索技能"。

**这就是为什么它叫"元能力"**——不是具体技能，而是教AI怎么找技能。

## 谁适合用

**先说清楚，这个东西不是所有人都需要**。

**适合的人**：
1、正在用Claude Code、Cursor、Windsurf等AI编程工具的开发者
2、想让AI Agent帮你找工具，而不是自己去翻文档的人
3、经常需要安装新技能包的人

**不适合的人**：
1、不用AI编程工具的人（find-skills需要AI Agent来发挥作用）
2、只想用中文交互的人（**搜索只支持英文关键词**）
3、完全不熟悉命令行的人

## 原版的三个大坑

官方版本来自Vercel：
```bash
npx skills add vercel-labs/skills@find-skills -g -y
```

**但是有三个大坑**。

**坑1：搜索只支持英文**

```bash
# ❌ 错误：中文搜索没有结果
npx skills find 数据分析
# 输出: No skills found for "数据分析"

# ✅ 正确：用英文关键词
npx skills find data analysis
# 输出: 找到6个相关技能
```

**坑2：触发不稳定，看AI心情**

因为AI是语义理解的，同样的话有时候触发，有时候不触发。

```
⚠️ "帮我找个做数据分析的工具" → 可能触发，也可能直接推荐Pandas
✅ "帮我搜索一个数据分析的skill" → 更容易触发find-skills搜索
✅ "用find-skills搜索data analysis" → 稳定触发
```

**建议**：想稳定触发，最好在话里带上"skill"这个词。

**坑3：Windows上完全不能用**

这是最致命的。

Claude Code在Windows上使用的Bash环境运行`npx skills find`会没有任何输出。
老金实测，搜索命令执行后返回空白，什么结果都没有。

这意味着**原版find-skills在Windows的Claude Code中基本不可用**。

## Windows用户的解决方案

老金fork了一份，修复了Windows兼容性问题。

**GitHub地址**：https://github.com/KimYx0207/findskill

**原理很简单**：让Claude Code用PowerShell来运行skills命令，而不是用默认的Bash环境。

### 安装方法

**步骤1：先装原版**
```bash
npx skills add vercel-labs/skills@find-skills -g -y
```

**步骤2：下载Windows版替换**

打开这个地址：
https://github.com/KimYx0207/findskill/blob/main/windows/SKILL.md

复制全部内容，替换到这个路径：
```
C:\Users\你的用户名\.agents\skills\find-skills\SKILL.md
```

**步骤3：重启Claude Code**

关掉Claude Code，重新打开。

**步骤4：验证安装**

对Claude Code说："帮我搜索一个数据分析的skill"

如果看到搜索结果，说明安装成功。

## 使用方法

### 触发方式

根据find-skills的SKILL.md，以下说法更容易触发搜索：
1、"find a skill for X"
2、"is there a skill that can..."
3、"搜索skill"
4、"找个skill"

**但因为AI是语义理解的，不带"skill"也可能触发**。
老金建议：想稳定触发，话里带上"skill"这个词更保险。

### 在AI Agent中使用

**你说**："帮我搜索一个数据分析的skill"

**AI Agent会**：
1、理解你要做数据分析
2、翻译成英文关键词"data analysis"
3、运行`npx skills find data analysis`（Windows版会用PowerShell）
4、展示搜索结果给你
5、问你要不要安装
6、你确认后，运行安装命令

### 手动使用CLI

如果你想自己搜索，也可以直接用命令行。

**Windows用户**（在PowerShell中）：
```powershell
npx skills find "data analysis"
```

**Mac/Linux用户**：
```bash
npx skills find data analysis
```

## 实战案例

### 案例1：数据分析

**搜索命令**：
```bash
npx skills find data analysis
```

**结果**：
```
davila7/claude-code-templates@exploratory-data-analysis
ailabs-393/ai-labs-claude-skills@data-analyst
pluginagentmarketplace/custom-plugin-python@pandas-data-analysis
```

**安装**：
```bash
npx skills add davila7/claude-code-templates@exploratory-data-analysis -g -y
```

### 案例2：做PPT

**搜索命令**：
```bash
npx skills find ppt
```

**结果**：
```
anthropics/skills@pptx
daymade/claude-code-skills@ppt-creator
jwynia/agent-skills@pptx-generator
```

**安装**：
```bash
npx skills add anthropics/skills@pptx -g -y
```

### 案例3：代码审查

**搜索命令**：
```bash
npx skills find code review
```

**结果**：
```
google-gemini/gemini-cli@code-reviewer
wshobson/agents@code-review-excellence
skillcreatorai/ai-agent-skills@code-review
```

**安装**：
```bash
npx skills add google-gemini/gemini-cli@code-reviewer -g -y
```

## 搜索关键词速查表

老金整理了一份中英文对照表，建议收藏。

**数据分析** → data analysis → 推荐exploratory-data-analysis
**做PPT** → ppt, presentation → 推荐pptx
**写文章** → writing → 推荐writing-skills
**代码审查** → code review → 推荐code-reviewer
**部署上线** → deploy → 推荐vercel-deployment
**写测试** → testing → 推荐webapp-testing
**做视频** → video, remotion → 推荐remotion-best-practices
**React开发** → react → 推荐vercel-react-best-practices
**Python开发** → python → 推荐python-testing-patterns
**前端设计** → frontend, design → 推荐frontend-design

**搜索技巧**：
1、用具体关键词："react testing"比"testing"效果好
2、试试同义词：如果"deploy"没找到，试试"deployment"
3、用英文：中文搜索没有结果

## 常见问题

**Q1：我说"帮我找个工具"，AI没有调用find-skills？**

因为AI是语义理解的，"找工具"这种说法有时候会触发，有时候不会。
想稳定触发，建议话里带上"skill"这个词：
"帮我搜索一个数据分析的skill" → 更容易触发find-skills搜索

**Q2：为什么搜索没有结果？**

1、用了中文关键词 → 改用英文
2、关键词太具体 → 试试更通用的词
3、网络问题 → 检查能否访问npm

**Q3：Windows上Claude Code搜索没有输出？**

用老金的Windows版本：https://github.com/KimYx0207/findskill

或者手动在PowerShell里运行：
```powershell
npx skills find "data analysis"
```

**Q4：怎么验证安装成功？**

```bash
npx skills list -g
```

会列出所有已安装的全局skills。

**Q5：skill和MCP有什么区别？**

Skill是知识和指南，教AI怎么做事（比如React最佳实践）。
MCP是工具和能力，让AI能做新的事（比如读取文件、调用API）。
简单说，Skill是"知道怎么做"，MCP是"能够做"。

**Q6：怎么卸载或更新skill？**

```bash
# 卸载
npx skills remove [skill名称] -g

# 更新
npx skills update
```

## 为什么find-skills这么火

24小时15.3K安装量，为什么这么火？

**原因1：解决根本问题**

Skills生态有几百个技能包，但你怎么知道该装哪个？
find-skills解决的就是"技能发现"这个根本问题。

**原因2：降低使用门槛**

以前你得手动翻文档、记名字、复制命令。
现在AI Agent读了find-skills的指南后，就知道怎么帮你搜索了。

**原因3：24小时排行榜数据**

第1名：find-skills（15.3K）
第2名：vercel-react-best-practices（5.8K）
第3名：remotion-best-practices（5.0K）

**第一名是第二名的2.6倍**。

## 老金总结

find-skills是个好东西，但原版有三个大坑：
1、搜索只支持英文
2、说"找工具"不触发
3、Windows上完全不能用

**Windows用户直接用老金的版本**：https://github.com/KimYx0207/findskill

装上之后，你的AI Agent就能帮你搜索skills.sh生态里的几百个技能了。

有问题随时交流，老金我会持续更新这个Windows兼容版。

---

## 参考来源

- find-skills官方：https://skills.sh/vercel-labs/skills/find-skills
- Windows兼容版（老金fork）：https://github.com/KimYx0207/findskill
- Skills CLI文档：https://skills.sh/docs
- Vercel Skills GitHub：https://github.com/vercel-labs/skills
- Skills v1.1.1更新日志：https://vercel.com/changelog/skills-v1-1-1-interactive-discovery-open-source-release-and-agent-support
