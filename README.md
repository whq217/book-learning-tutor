# book-learning-tutor · 读书引导学习技能

一个 [Claude Code](https://claude.com/claude-code) 技能（Skill）：让 AI 用**费曼方式**带你真正读透一本书。

不是摘要，不是伴读，是「讲解 → 确认理解 → 出题测试 → 答错重讲」的完整学习闭环。

## 它解决什么问题

大多数人读完一本书的状态是：划了很多线，讲不出三句话。

这个技能把学习过程强制改成「构建即理解」——每讲完一段，你要用自己的话复述；每章结束，要答题通过才能进入下一章。讲不清楚，就是还没懂，AI 换方式重讲。

## 工作流程

```
Phase 0: 材料解析与拆章（生成学习路线图）
    ↓
Phase 1: 逐章讲解（核心循环）
    讲解 → 确认理解 → 问答 → 章节测试
    ↓通过                    ↓未通过
Phase 3: 全书总结        Phase 2: 重讲机制（换类比→换结构→苏格拉底式，最多3次）
    ↓
Phase 4: 学习成果固化（可选，生成笔记归档）
```

特点：

- **费曼式讲解**：先场景后概念，每个抽象概念配日常类比，并指出「类比到哪里就不成立」
- **真理解门槛**：章节测试不过不进下一章，但重讲 3 次仍不懂会标记待复习、先继续，不死磕
- **不考记忆考理解**：不出「第X页说了什么」这类题，只出复述/应用/辨析/反例/推导五类题
- **跨会话可恢复**：每章生成学习快照，粘贴回来就能从断点继续

## 安装

### 方式一：全局安装（所有项目可用）

```bash
git clone https://github.com/<你的用户名>/book-learning-tutor-public.git
mkdir -p ~/.claude/skills
cp -r book-learning-tutor-public/book-learning-tutor ~/.claude/skills/
```

Windows (PowerShell)：

```powershell
git clone https://github.com/<你的用户名>/book-learning-tutor-public.git
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills"
Copy-Item -Recurse book-learning-tutor-public\book-learning-tutor "$env:USERPROFILE\.claude\skills\"
```

### 方式二：项目级安装（仅当前项目）

把 `book-learning-tutor/` 文件夹复制到你的项目下：

```
你的项目/.claude/skills/book-learning-tutor/
```

## 使用

安装后对 Claude 说：

- 「帮我学这本书」/「带我读《XX》」
- 「我想搞懂这个材料」（扔一个文件或链接）
- 「这个材料有点深，帮我吃透」

AI 会先生成学习路线图，问你从哪章开始，然后进入讲解-测试循环。

不想被考？说「别考我」，AI 只讲解不出题。

## 文件结构

```
book-learning-tutor/
├── SKILL.md                              # 技能主文件（流程+规则）
└── references/
    ├── question-templates.md             # 五种题型出题模板
    └── learning-notes-template.md        # 学习笔记模板
```

## License

MIT
