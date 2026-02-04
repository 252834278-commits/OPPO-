# Skills 技能库

这是一个技能文档仓库，用于管理各类专业分析和工作流技能。

## 📁 目录结构

```
.
├── README.md                   # 主说明文档
└── skills/                     # 技能文档目录
    ├── system-weather-competitive-analysis.md  # 系统天气应用竞品分析
    └── (未来新增的技能文档...)
```

## 📋 技能列表

### 1. 系统天气应用竞品分析 (system-weather-competitive-analysis)

**文件**: `skills/system-weather-competitive-analysis.md`

**描述**: 对系统天气应用进行全面的竞品分析与对标，输出专业的 Markdown 报告。

**覆盖范围**:
- iOS 天气（Apple Weather）
- 小米天气
- 鸿蒙纯血版天气（HarmonyOS NEXT）
- 荣耀天气
- 墨迹天气

**核心能力**:
- 功能矩阵对比：统一维度的功能点对比分析
- 体验走查：详细的用户体验走查与证据点收集
- 差异洞察：识别关键差异与产品机会点
- 优先级建议：P0/P1/P2 级别的改进建议与落地方案

**使用场景**: 竞品分析、对标、天气 app 评测

---

## 🆕 如何新增技能

### 方法 1: 单个技能文件

如果技能文档较简单，直接在 `skills/` 目录下创建 Markdown 文件：

```bash
# 创建新技能文档
touch skills/your-skill-name.md

# 编辑技能文档，包含以下结构：
# - 技能名称和描述
# - 使用场景
# - 核心功能
# - 操作步骤
# - 输出示例
```

**命名规范**:
- 使用小写字母和连字符（kebab-case）
- 例如：`e-commerce-conversion-optimization.md`
- 例如：`user-interview-analysis.md`

### 方法 2: 复杂技能目录

如果技能包含多个文件（模板、示例、配置等），创建子目录：

```bash
skills/
├── complex-skill-name/
│   ├── README.md           # 技能主文档
│   ├── templates/          # 模板文件
│   ├── examples/           # 示例文件
│   └── configs/            # 配置文件
```

### 新增技能检查清单

- [ ] 在 `skills/` 目录下创建文件或子目录
- [ ] 技能文档包含清晰的 frontmatter（name, description）
- [ ] 更新主 README.md，在技能列表中添加新条目
- [ ] 提交代码：`git add . && git commit -m "feat: add [技能名称] skill"`
- [ ] 推送到 GitHub：`git push origin main`

## 📝 技能文档模板

```markdown
---
name: your-skill-name
description: 简要描述技能的用途和适用场景
---

# 技能名称

## 快速开始

简要说明如何使用此技能...

## 使用场景

列出适用的场景和触发关键词...

## 核心功能

1. 功能点 1
2. 功能点 2
3. 功能点 3

## 操作步骤

详细的操作流程...

## 输出示例

展示预期的输出格式...
```

## 🔄 版本管理

所有技能文档都通过 Git 进行版本管理：

- **提交规范**: 使用 [Conventional Commits](https://www.conventionalcommits.org/) 格式
  - `feat: 添加新技能`
  - `fix: 修复技能文档错误`
  - `docs: 更新说明文档`
  - `refactor: 重构技能结构`

- **分支管理**: 
  - `main`: 主分支，存放稳定版本
  - `develop`: 开发分支（可选）
  - `feature/*`: 功能分支

## 📊 技能分类

未来可以按以下类别组织技能：

- **产品分析类**: 竞品分析、用户研究、数据分析
- **设计类**: UI/UX 评审、设计系统、交互原型
- **技术类**: 代码审查、架构设计、性能优化
- **运营类**: 内容策略、增长黑客、社群运营

## 📞 贡献指南

1. Fork 本仓库
2. 创建特性分支：`git checkout -b feature/new-skill`
3. 提交更改：`git commit -m "feat: add new skill"`
4. 推送分支：`git push origin feature/new-skill`
5. 创建 Pull Request

## 📄 许可证

待定

## 更新日志

- **2026-02-04**: 初始化仓库，添加系统天气应用竞品分析技能
