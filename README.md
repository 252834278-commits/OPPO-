# Skills 技能库

这是一个符合 Claude Code 标准的技能文档仓库，遵循 [Agent Skills](https://agentskills.io/) 开放标准。

## 📁 目录结构（Claude Code 标准）

```
.
├── README.md                   # 主说明文档
├── STRUCTURE.md                # 详细结构说明
└── .claude/                    # Claude Code 配置目录 ⭐
    └── skills/                 # 技能文档目录（Claude Code 标准位置）
        ├── TEMPLATE.md         # 技能模板参考
        └── system-weather-competitive-analysis/  # 具体技能目录
            └── SKILL.md        # 技能主文档（必需）
```

## 🎯 关键说明

### Claude Code Skills 标准

根据 [Claude Code 官方文档](https://code.claude.com/docs/en/skills)，Skills 必须放置在以下位置：

| 位置 | 路径 | 适用范围 |
|------|------|----------|
| **项目级** | `.claude/skills/<skill-name>/SKILL.md` | ✅ 仅此项目（推荐提交到版本控制） |
| 个人级 | `~/.claude/skills/<skill-name>/SKILL.md` | 所有你的项目 |
| 企业级 | 见管理设置 | 组织内所有用户 |
| 插件 | `<plugin>/skills/<skill-name>/SKILL.md` | 插件启用的地方 |

**本仓库使用项目级配置**（`.claude/skills/`），适合团队协作和版本控制。

### 技能目录结构

每个技能是一个独立目录，必须包含 `SKILL.md`：

```
system-weather-competitive-analysis/
├── SKILL.md           # 主指令文档（必需）
├── template.md        # 模板文件（可选）
├── examples/          # 示例输出（可选）
│   └── sample.md
└── scripts/           # 辅助脚本（可选）
    └── helper.py
```

## 📋 当前技能列表

### 1. 系统天气应用竞品分析 (system-weather-competitive-analysis)

**路径**: `.claude/skills/system-weather-competitive-analysis/SKILL.md`

**描述**: 对系统天气应用进行全面的竞品分析与对标，输出专业的 Markdown 报告。

**覆盖范围**:
- iOS 天气（Apple Weather）
- 小米天气
- 鸿蒙纯血版天气（HarmonyOS NEXT）
- 荣耀天气
- 墨迹天气

**触发方式**:
- 自动触发：当你提到"竞品分析"、"对标"、"天气 app" 等关键词
- 手动调用：`/system-weather-competitive-analysis`

**核心能力**:
- 功能矩阵对比：统一维度的功能点对比分析
- 体验走查：详细的用户体验走查与证据点收集
- 差异洞察：识别关键差异与产品机会点
- 优先级建议：P0/P1/P2 级别的改进建议与落地方案

---

## 🆕 如何新增技能

### Step 1: 创建技能目录

```bash
cd /home/user/webapp
mkdir -p .claude/skills/your-skill-name
```

### Step 2: 创建 SKILL.md

```bash
# 可以参考模板
cp .claude/skills/TEMPLATE.md .claude/skills/your-skill-name/SKILL.md
```

### Step 3: 编辑 SKILL.md

最小化示例：

```markdown
---
name: your-skill-name
description: 简要说明这个技能做什么，Claude 用这个描述来判断何时使用
---

# Your Skill Instructions

详细的指令内容...
```

### Step 4: 更新 README.md

在"当前技能列表"部分添加新技能的说明。

### Step 5: 提交到 Git

```bash
git add .claude/skills/your-skill-name/ README.md
git commit -m "feat(skills): add your-skill-name"
git push origin main
```

## 📝 SKILL.md Frontmatter 配置

```yaml
---
name: skill-name                           # 技能名称（可选，默认使用目录名）
description: 技能描述                       # 推荐填写，Claude 用来判断何时使用
argument-hint: [参数说明]                   # 自动补全提示（可选）
disable-model-invocation: true             # 禁止 Claude 自动调用（可选）
user-invocable: false                       # 隐藏在 / 菜单中（可选）
allowed-tools: Read, Grep, Bash            # 允许使用的工具（可选）
model: opus-4                               # 指定模型（可选）
context: fork                               # 在子代理中运行（可选）
agent: Explore                              # 子代理类型（可选）
---
```

## 🎮 使用技能

### Claude 自动调用
当你的对话内容匹配技能的 `description` 时，Claude 会自动加载相关技能。

### 手动调用
```
/skill-name                    # 调用技能
/skill-name arg1 arg2         # 传递参数
```

### 查看可用技能
```
What skills are available?     # 让 Claude 列出所有技能
```

## 📚 技能类型建议

### 参考型技能（Reference）
添加知识、规范、模式，Claude 在工作时应用。
- 代码规范
- API 约定
- 领域知识

```yaml
---
name: api-conventions
description: API 设计规范
---
```

### 任务型技能（Task）
具体的操作指令，通常手动调用。
- 部署流程
- 提交规范
- 代码生成

```yaml
---
name: deploy
description: 部署应用到生产环境
disable-model-invocation: true  # 防止 Claude 自动触发
---
```

## 🔧 高级功能

### 动态上下文注入
使用 `` !`command` `` 语法在发送给 Claude 前执行命令：

```markdown
---
name: pr-summary
description: 总结 PR 变更
---

## PR 上下文
- PR diff: !`gh pr diff`
- PR comments: !`gh pr view --comments`

分析这个 PR...
```

### 参数替换
```markdown
Fix GitHub issue $ARGUMENTS
# 或使用位置参数
Migrate $0 from $1 to $2
```

### 子代理执行
```yaml
---
context: fork
agent: Explore
---
```

## 🔗 相关资源

- 📘 [Claude Code Skills 官方文档](https://code.claude.com/docs/en/skills)
- 📗 [Agent Skills 开放标准](https://agentskills.io/)
- 📙 [Awesome Claude Skills](https://github.com/travisvn/awesome-claude-skills)

## 📊 仓库信息

- **位置**: `/home/user/webapp/`
- **GitHub**: https://github.com/252834278-commits/OPPO-.git
- **技能数量**: 1 个 + 1 个模板
- **最后更新**: 2026-02-04

## 🤝 贡献指南

1. Fork 本仓库
2. 创建技能分支：`git checkout -b feat/new-skill`
3. 在 `.claude/skills/` 下创建新技能
4. 更新 README.md
5. 提交：`git commit -m "feat(skills): add new-skill"`
6. 推送并创建 Pull Request

## 版本历史

- **2026-02-04**: 重构为 Claude Code 标准结构（`.claude/skills/`）
- **2026-02-04**: 初始化仓库，添加系统天气应用竞品分析技能
