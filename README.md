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
        ├── system-weather-competitive-analysis/  # 天气应用竞品分析
        │   └── SKILL.md
        ├── mobile-weather-app-prd/              # 天气应用 PRD 生成
        │   └── SKILL.md
        └── weather-app-prd-validator/           # 天气应用 PRD 校验
            └── SKILL.md
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

### 2. 手机系统天气应用 PRD 生成 (mobile-weather-app-prd)

**路径**: `.claude/skills/mobile-weather-app-prd/SKILL.md`

**描述**: 生成手机系统天气应用的产品需求文档（PRD），包含完整的功能模块定义、界面设计规范、交互要求和技术实现要点。

**适用场景**:
- 为天气应用编写 PRD
- 定义功能需求
- 设计天气应用功能模块  
- 创建天气应用产品文档

**触发方式**:
- 自动触发：当你提到"PRD"、"产品需求文档"、"功能定义"、"天气应用设计" 等关键词
- 手动调用：`/mobile-weather-app-prd`

**核心能力**:
- 完整 PRD 结构：按标准模板生成文档
- 功能模块库：9 大核心模块预定义
- 设计规范：界面、交互、颜色字体规范
- 用户洞察驱动：基于真实用户调研
- 竞品对标：强制覆盖四大竞品对比
- 合规检查：隐私合规、埋点、升级回落

---

### 2. 手机系统天气应用 PRD 生成 (mobile-weather-app-prd)

**路径**: `.claude/skills/mobile-weather-app-prd/SKILL.md`

**描述**: 生成手机系统天气应用的产品需求文档（PRD），包含完整的功能模块定义、界面设计规范、交互要求和技术实现要点。

**适用场景**:
- 为天气应用编写 PRD
- 定义功能需求
- 设计天气应用功能模块
- 创建天气应用产品文档

**触发方式**:
- 自动触发：当你提到"PRD"、"产品需求文档"、"功能定义"、"天气应用设计" 等关键词
- 手动调用：`/mobile-weather-app-prd`

**核心能力**:
- **完整 PRD 结构**：按标准模板生成包含需求概况、产品策略、功能设计、合规要求的完整文档
- **功能模块库**：预定义 9 大天气应用核心模块（当前天气、逐小时预报、每日预报、空气质量、生活指数等）
- **设计规范**：包含界面设计、交互规范、颜色字体规范
- **用户洞察驱动**：基于真实用户调研（通勤人群、户外爱好者、精致妈妈等）的痛点和场景
- **竞品对标要求**：强制覆盖小米天气、华为天气、荣耀天气、墨迹天气的功能对比
- **合规检查清单**：涵盖隐私合规、进网要求、埋点需求、升级回落策略

**功能模块覆盖**:
1. 当前天气概览
2. 逐小时天气预报（24小时）
3. 每日天气预报（7-15天）
4. 空气质量详情（AQI + 污染物）
5. 详细气象数据（紫外线、体感、湿度、风力、气压、能见度）
6. 日出日落时间
7. 生活建议/指数（穿衣、带伞、护肤、运动等）
8. 位置管理（多城市切换）
9. 天气预警（多级别预警系统）

**特色功能**:
- 用户故事库：基于 18 人线下座谈会的真实用户痛点
- 生活指数口径：华风/墨迹双源数据口径参考
- 预警类型枚举：完整的气象预警类型和等级定义
- 首页轮播位规则：卡片优先级和触发条件详细定义

---

### 3. 天气应用 PRD 校验 (weather-app-prd-validator)

**路径**: `.claude/skills/weather-app-prd-validator/SKILL.md`

**描述**: 对天气 App PRD 进行完整性、一致性、可测试性和可行性校验，确保文档可开发、可测试、可验收。

**适用场景**:
- 校验/评审天气 App PRD
- 检查验收标准和边界条件
- 审查埋点、预警、生活指数等需求
- 评估隐私合规与开发就绪度

**触发方式**:
- 自动触发：当你提到"PRD 校验"、"PRD 评审"、"验收标准"、"边界条件"、"埋点检查" 等关键词
- 手动调用：`/weather-app-prd-validator`

**核心能力**:
- **硬校验**：对照天气 PRD 模版做必填项检查（缺失即 P0/P1）
- **天气专项校验**：数据口径/定位/预警通知/生活指数/弱网离线/NFR/合规
- **可复制改写**：输出可直接落回 PRD 的改写片段
- **严重度分级**：P0 阻塞 / P1 严重 / P2 一般 / P3 轻微 / 建议
- **评分卡**：8 个维度的 0-5 分评估

**校验维度**:
1. 模版必填项硬校验（13 个 Gate）
2. 原子需求可测试性检查
3. 一致性与口径检查
4. 天气专项校验（数据源/定位/预警/生活指数/端侧能力/NFR/合规）

**输出格式**:
- PRD 校验结论（就绪度/阻塞项/风险）
- 章节覆盖率表
- 8 维度评分卡
- 待确认信息清单
- 逐章点评
- 问题清单（按严重度排序）
- 可复制的 PRD 改写建议

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
- **技能数量**: 3 个 + 1 个模板
- **最后更新**: 2026-02-09

## 🤝 贡献指南

1. Fork 本仓库
2. 创建技能分支：`git checkout -b feat/new-skill`
3. 在 `.claude/skills/` 下创建新技能
4. 更新 README.md
5. 提交：`git commit -m "feat(skills): add new-skill"`
6. 推送并创建 Pull Request

## 版本历史

- **2026-02-09**: 添加天气应用 PRD 校验技能 (weather-app-prd-validator)
- **2026-02-04**: 添加手机系统天气应用 PRD 生成技能
- **2026-02-04**: 重构为 Claude Code 标准结构（`.claude/skills/`）
- **2026-02-04**: 初始化仓库，添加系统天气应用竞品分析技能
