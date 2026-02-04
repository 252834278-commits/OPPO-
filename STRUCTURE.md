# Claude Code Skills 仓库结构说明

## 📂 正确的目录结构（Claude Code 标准）

```
OPPO-/                                    # GitHub 仓库根目录
├── README.md                             # 主说明文档
├── STRUCTURE.md                          # 本文件
└── .claude/                              # ⭐ Claude Code 配置目录
    └── skills/                           # ⭐ 技能目录（标准位置）
        ├── TEMPLATE.md                   # 技能模板参考
        └── system-weather-competitive-analysis/  # 具体技能
            └── SKILL.md                  # 技能主文档（必需）
```

## 🎯 为什么必须是 `.claude/skills/`？

### Claude Code 的标准查找路径

根据 [官方文档](https://code.claude.com/docs/en/skills#where-skills-live)，Claude Code 会在以下位置查找技能：

| 优先级 | 位置 | 路径 | 适用范围 |
|--------|------|------|----------|
| 1️⃣ 最高 | 企业级 | 管理设置配置 | 组织内所有用户 |
| 2️⃣ 高 | 个人级 | `~/.claude/skills/<skill-name>/` | 你的所有项目 |
| 3️⃣ 中 | **项目级** | **`.claude/skills/<skill-name>/`** | **✅ 仅此项目** |
| 4️⃣ 低 | 插件 | `<plugin>/skills/<skill-name>/` | 插件启用位置 |

**本仓库使用项目级配置**，原因：
- ✅ 可以提交到版本控制（Git）
- ✅ 团队成员共享相同技能
- ✅ 技能随项目分发
- ✅ 不同项目可以有不同技能

### 之前的错误 ❌

```
OPPO-/
├── skills/                    # ❌ 错误！Claude 不会读取这个位置
│   └── system-weather-competitive-analysis.md
```

### 现在的正确结构 ✅

```
OPPO-/
└── .claude/                   # ✅ 正确！Claude Code 标准位置
    └── skills/
        └── system-weather-competitive-analysis/
            └── SKILL.md       # 必须命名为 SKILL.md
```

## 📋 技能目录的标准结构

### 最小化技能（单文件）

```
.claude/skills/simple-skill/
└── SKILL.md                   # 唯一必需的文件
```

### 完整技能（多文件）

```
.claude/skills/complex-skill/
├── SKILL.md                   # 主指令文档（必需）
├── template.md                # Claude 要填充的模板
├── examples/                  # 示例输出
│   ├── example-1.md
│   └── example-2.md
├── scripts/                   # 辅助脚本
│   ├── helper.py
│   └── validator.sh
└── docs/                      # 详细文档
    └── reference.md
```

### SKILL.md 必需格式

```markdown
---
name: skill-name               # 可选，默认使用目录名
description: 描述              # 推荐，Claude 用来判断何时使用
---

# 技能指令内容

详细说明...
```

## 🆕 新增技能的标准流程

### 方法 1: 简单技能（单个 SKILL.md）

```bash
# 1. 创建技能目录
cd /home/user/webapp
mkdir -p .claude/skills/your-skill-name

# 2. 创建 SKILL.md（可以从模板复制）
cp .claude/skills/TEMPLATE.md .claude/skills/your-skill-name/SKILL.md

# 3. 编辑 SKILL.md
# 填写 frontmatter 和指令内容...

# 4. 更新 README.md
# 在技能列表中添加说明...

# 5. 提交
git add .claude/skills/your-skill-name/ README.md
git commit -m "feat(skills): add your-skill-name"
git push origin main
```

### 方法 2: 复杂技能（多文件）

```bash
# 1. 创建完整目录结构
cd /home/user/webapp
mkdir -p .claude/skills/complex-skill/{examples,scripts,docs}

# 2. 创建必需的 SKILL.md
cat > .claude/skills/complex-skill/SKILL.md << 'EOF'
---
name: complex-skill
description: 详细描述
---

# Complex Skill

主指令...

## 附加资源
- 详细文档：见 [reference.md](docs/reference.md)
- 示例：见 [examples/](examples/)
- 脚本：见 [scripts/](scripts/)
EOF

# 3. 创建其他文件
touch .claude/skills/complex-skill/examples/example-1.md
touch .claude/skills/complex-skill/scripts/helper.py
touch .claude/skills/complex-skill/docs/reference.md

# 4. 提交
git add .claude/skills/complex-skill/
git commit -m "feat(skills): add complex-skill with supporting files"
git push origin main
```

## 📝 命名规范

### 技能目录命名
使用 **kebab-case**（小写 + 连字符）：

**✅ 好的示例**:
- `system-weather-competitive-analysis`
- `user-interview-synthesis`
- `api-security-audit`
- `e-commerce-conversion-optimization`

**❌ 不好的示例**:
- `SystemWeatherAnalysis` （驼峰式）
- `system_weather_analysis` （下划线）
- `skill1` （无意义）
- `SKILL` （大写，且与文件名冲突）

### 文件命名
- 主文档：**必须**命名为 `SKILL.md`（大写）
- 其他文件：使用小写和连字符，如 `template.md`、`example-output.md`

## 🎮 Claude Code 如何使用技能

### 1. 自动发现
Claude Code 启动时会扫描：
```
.claude/skills/*/SKILL.md
```

### 2. 加载到上下文
- 技能的 `description` 始终在 Claude 的上下文中
- 完整的 SKILL.md 内容在被调用时加载

### 3. 调用方式

#### 自动调用
当你的对话匹配 `description` 时：
```
用户: 帮我做一个天气 app 的竞品分析
Claude: （自动加载 system-weather-competitive-analysis 技能）
```

#### 手动调用
```
/system-weather-competitive-analysis
/api-security-audit ProjectX
/deploy production v2.0
```

#### 禁止自动调用
在 frontmatter 中设置：
```yaml
---
disable-model-invocation: true
---
```

## 🔧 高级功能

### 参数传递
```markdown
---
name: fix-issue
---

Fix GitHub issue $ARGUMENTS
# 或
Fix issue $0 in $1 branch
```

调用：
```
/fix-issue 123
/fix-issue 456 main
```

### 动态命令执行
```markdown
---
name: pr-summary
---

## PR 信息
- Diff: !`gh pr diff`
- Status: !`gh pr view --json state`

分析以上信息...
```

命令在发送给 Claude **之前**执行，Claude 只看到结果。

### 子代理执行
```yaml
---
name: deep-research
context: fork              # 在隔离的子代理中运行
agent: Explore             # 使用 Explore 代理
---
```

### 工具限制
```yaml
---
allowed-tools: Read, Grep, Glob
---
```

## 📊 与其他 Claude Code 功能的关系

| 功能 | 位置 | 用途 |
|------|------|------|
| **Skills** | `.claude/skills/` | 可重用的指令和工作流 |
| **CLAUDE.md** | `.claude/CLAUDE.md` | 项目级持久上下文 |
| **Subagents** | `.claude/agents/` | 自定义子代理配置 |
| **Hooks** | `.claude/hooks/` | 工具事件自动化 |
| **Plugins** | `~/.claude/plugins/` | 扩展功能包 |

## 🔍 故障排查

### 技能不触发
1. 检查 `description` 是否包含相关关键词
2. 运行 `What skills are available?` 查看是否列出
3. 尝试手动调用：`/skill-name`
4. 检查文件路径是否正确：`.claude/skills/<name>/SKILL.md`

### Claude 看不到所有技能
技能描述会加载到上下文，默认限制 15,000 字符。
- 运行 `/context` 查看是否有警告
- 设置环境变量：`SLASH_COMMAND_TOOL_CHAR_BUDGET=30000`

### 技能触发太频繁
1. 使 `description` 更具体
2. 添加 `disable-model-invocation: true`

## 🌍 技能分发策略

### 项目级（本仓库）
```bash
# 提交到 Git
git add .claude/skills/
git commit -m "feat(skills): add new skill"
git push

# 团队成员 pull 后自动可用
git pull
```

### 个人级
```bash
# 创建在个人目录
mkdir -p ~/.claude/skills/my-skill
cat > ~/.claude/skills/my-skill/SKILL.md << 'EOF'
---
name: my-skill
description: 我的私人技能
---
EOF

# 所有项目都能用
```

### 插件级
```bash
# 在插件中创建
~/.claude/plugins/my-plugin/
└── skills/
    └── plugin-skill/
        └── SKILL.md

# 使用时带命名空间
/my-plugin:plugin-skill
```

## 📚 参考资源

- 🔗 [Claude Code Skills 官方文档](https://code.claude.com/docs/en/skills)
- 🔗 [Agent Skills 开放标准](https://agentskills.io/)
- 🔗 [Awesome Claude Skills 精选列表](https://github.com/travisvn/awesome-claude-skills)
- 🔗 [Claude Code 自定义指南](https://alexop.dev/posts/claude-code-customization-guide-claudemd-skills-subagents/)

## 💡 最佳实践

### DO ✅
1. **描述要清晰**：让 Claude 能准确判断何时使用
2. **指令要具体**：明确的步骤和预期输出
3. **提交到版本控制**：团队共享技能
4. **使用模板**：保持一致性
5. **文档化**：在 README 中列出所有技能

### DON'T ❌
1. **不要放错位置**：必须在 `.claude/skills/` 下
2. **不要用错文件名**：必须是 `SKILL.md`（不是 `skill.md`）
3. **不要省略 description**：Claude 需要它来判断何时使用
4. **不要让技能太长**：考虑拆分或使用支持文件
5. **不要忘记更新文档**：保持 README 同步

## 🚀 快速参考

```bash
# 查看当前结构
cd /home/user/webapp && find .claude -type f

# 创建新技能
mkdir -p .claude/skills/new-skill
cat > .claude/skills/new-skill/SKILL.md << 'EOF'
---
name: new-skill
description: What it does
---
# Instructions
...
EOF

# 验证技能
# 在 Claude Code 中输入：
What skills are available?

# 测试技能
/new-skill test arguments
```

---

**最后更新**: 2026-02-04  
**维护者**: 252834278-commits  
**仓库**: https://github.com/252834278-commits/OPPO-.git
