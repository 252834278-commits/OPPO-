# Skills 仓库结构说明

## 📂 当前目录结构

```
OPPO-/                          # GitHub 仓库根目录
├── README.md                   # 主说明文档（包含使用指南）
└── skills/                     # 技能文档目录
    ├── TEMPLATE.md             # 技能文档标准模板
    └── system-weather-competitive-analysis.md  # 系统天气应用竞品分析
```

## 🎯 为什么这样组织？

### 之前的问题
- ❌ `SKILL.md` 直接放在根目录，不够清晰
- ❌ 多个技能文档会混乱
- ❌ 没有统一的组织规范

### 现在的优势
- ✅ `skills/` 目录集中管理所有技能文档
- ✅ 文件名清晰表达技能用途
- ✅ 有标准模板可以参考
- ✅ README 提供完整的使用指南

## 📝 新增技能的标准流程

### 方式 1: 简单技能（单个文件）

```bash
# 1. 复制模板
cd /home/user/webapp
cp skills/TEMPLATE.md skills/your-new-skill-name.md

# 2. 编辑技能文档
# 填写实际内容...

# 3. 更新 README.md，在技能列表中添加新条目

# 4. 提交到 Git
git add skills/your-new-skill-name.md README.md
git commit -m "feat: add your-new-skill-name skill"

# 5. 推送到 GitHub
git push origin main
```

### 方式 2: 复杂技能（多个文件）

```bash
# 1. 创建技能子目录
cd /home/user/webapp
mkdir -p skills/complex-skill-name

# 2. 创建相关文件
touch skills/complex-skill-name/README.md
mkdir -p skills/complex-skill-name/{templates,examples,configs}

# 3. 编辑所有必要文件

# 4. 更新主 README.md

# 5. 提交推送
git add skills/complex-skill-name/ README.md
git commit -m "feat: add complex-skill-name skill"
git push origin main
```

## 🗂️ 未来可能的扩展结构

```
OPPO-/
├── README.md
├── skills/
│   ├── TEMPLATE.md
│   │
│   # 产品分析类
│   ├── product-analysis/
│   │   ├── system-weather-competitive-analysis.md
│   │   ├── user-behavior-analysis.md
│   │   └── market-research.md
│   │
│   # 设计类
│   ├── design/
│   │   ├── ui-ux-review.md
│   │   └── design-system-audit.md
│   │
│   # 技术类
│   ├── tech/
│   │   ├── code-review.md
│   │   └── performance-optimization.md
│   │
│   # 运营类
│   └── operations/
│       ├── content-strategy.md
│       └── growth-hacking.md
│
├── examples/                    # 示例输出目录
│   └── weather-analysis-2026-02-04.md
│
└── docs/                        # 额外文档
    ├── contribution-guide.md
    └── best-practices.md
```

## 📋 命名规范

### 技能文件命名
- 使用 kebab-case（小写+连字符）
- 清晰描述技能用途
- 避免使用缩写

**好的示例**:
- ✅ `system-weather-competitive-analysis.md`
- ✅ `user-interview-synthesis.md`
- ✅ `e-commerce-conversion-optimization.md`

**不好的示例**:
- ❌ `SKILL.md` （不明确）
- ❌ `weatherAnalysis.md` （使用驼峰式）
- ❌ `skill_1.md` （无意义命名）

### 提交信息规范
遵循 [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <subject>

<body>

<footer>
```

**类型（type）**:
- `feat`: 新功能（新增技能）
- `fix`: 修复（修正技能文档错误）
- `docs`: 文档（更新 README）
- `refactor`: 重构（调整目录结构）
- `test`: 测试
- `chore`: 杂项

**示例**:
```
feat(skills): add user-interview-synthesis skill

- Add comprehensive user interview analysis framework
- Include synthesis methods and insight extraction
- Provide persona generation templates

Closes #123
```

## 🔄 版本管理

### Git 分支策略
- `main`: 稳定版本，已验证的技能
- `develop`: 开发分支（可选）
- `feature/skill-name`: 新技能开发分支

### 工作流程
```bash
# 1. 从 main 创建新分支
git checkout -b feature/new-skill-name

# 2. 开发新技能
# ... 编辑文件 ...

# 3. 提交更改
git add .
git commit -m "feat: add new-skill-name skill"

# 4. 推送分支
git push origin feature/new-skill-name

# 5. 创建 Pull Request（在 GitHub 上）

# 6. 审核通过后合并到 main
```

## 📊 当前状态

**仓库信息**:
- 📍 位置: `/home/user/webapp/`
- 🔗 远程: `https://github.com/252834278-commits/OPPO-.git`
- 🌿 分支: `main`
- 📦 技能数量: 1 个（+ 1 个模板）

**最近提交**:
```
73b3445 refactor: reorganize skills structure
e469012 docs: add README for weather analysis skill
bf9cb1a feat: add system weather competitive analysis skill
```

## 💡 使用建议

1. **创建新技能前**: 先查看 `skills/TEMPLATE.md`
2. **命名要清晰**: 让别人一眼知道这个技能是做什么的
3. **更新 README**: 每次新增技能都要更新主 README
4. **及时提交**: 完成一个技能立即提交，不要积累
5. **写好描述**: commit message 要清楚说明做了什么

## 🔗 相关链接

- 📘 [Conventional Commits 规范](https://www.conventionalcommits.org/)
- 📗 [Markdown 语法指南](https://www.markdownguide.org/)
- 📙 [Git 最佳实践](https://git-scm.com/book/zh/v2)

---

**最后更新**: 2026-02-04
**维护者**: 252834278-commits
