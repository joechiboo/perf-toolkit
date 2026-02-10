# SDD + Agent Skills 框架使用指南

## 框架概覽

本專案採用 **SDD（Spec-Driven Development）** 結合 **Agent Skills** 的雙軌開發模式：

```
                    ┌──────────────┐
                    │  CLAUDE.md   │  ← AI 自動載入的入口
                    │  (膠水層)     │
                    └──────┬───────┘
                           │
              ┌────────────┼────────────┐
              ▼                         ▼
    ┌──────────────────┐     ┌──────────────────┐
    │   .specify/       │     │  .claude/skills/  │
    │   (WHAT + WHY)    │     │  (HOW)            │
    │                   │     │                   │
    │  constitution.md  │     │  sdd/SKILL.md     │
    │  specification.md │     │  [其他skills]      │
    └──────────────────┘     └──────────────────┘
              │                         │
              └────────────┬────────────┘
                           ▼
                    ┌──────────────┐
                    │   src/       │  ← 實際程式碼
                    │   tests/     │  ← 測試
                    │   docs/      │  ← 詳細文檔
                    └──────────────┘
```

## 各檔案的職責

| 檔案 | 職責 | 誰維護 | 何時更新 |
|------|------|--------|---------|
| `CLAUDE.md` | 告訴 AI 這個專案怎麼協作 | 開發者 | 工作流程變更時 |
| `constitution.md` | 開發原則、技術限制 | 開發者 | 技術決策變更時 |
| `specification.md` | 功能需求、使用者故事、階段規劃 | PM/開發者 | 需求變更時 |
| `SKILL.md` | AI 導航某個特定領域的操作指引 | 開發者 | 模組成熟後 |

## 使用流程

### 新專案初始化

```bash
# 1. 建立 SDD 結構
mkdir -p .specify/memory
mkdir -p .claude/skills/sdd

# 2. 填寫核心文件
#    constitution.md → 開發原則
#    specification.md → 功能需求

# 3. 建立 AI 入口
#    CLAUDE.md → 專案級指令
#    skills/sdd/SKILL.md → 工作流導航
```

### 日常開發

1. **開始任務前** — AI 讀取 constitution + specification 了解上下文
2. **實作中** — 參考 SKILL.md 中的操作指引
3. **完成後** — 更新 specification 中的 checkbox，必要時更新 constitution

### 新增模組

當專案長出新的獨立模組時：

```bash
# 建立模組專屬 skill
mkdir -p .claude/skills/[module-name]

# 撰寫 SKILL.md
# - 概述模組功能
# - 列出核心文件路徑
# - 提供常用操作指引
# - 記錄故障排除方案
```

## SDD 與 Agent Skills 的分工

```
┌─────────────────────────────────────────────────────┐
│  提問                        │  找哪裡？             │
├─────────────────────────────────────────────────────┤
│  這個專案要做什麼？           │  specification.md     │
│  開發有什麼限制？             │  constitution.md      │
│  AI 怎麼跟我協作？            │  CLAUDE.md           │
│  這個模組怎麼操作？           │  skills/xxx/SKILL.md  │
│  完整技術細節？               │  docs/               │
│  實際程式碼？                 │  src/                │
└─────────────────────────────────────────────────────┘
```

## 最佳實踐

### Constitution（開發憲章）
- 寫具體可執行的原則，不要太抽象
- 包含可驗證的品質標準
- 技術選型確定後及時記錄

### Specification（產品規格）
- 從使用者視角撰寫
- 用 checkbox 追蹤實作進度
- 分階段規劃，避免一次塞太多

### SKILL.md
- 保持精簡，只放 AI 需要的導航資訊
- 用相對路徑連結到詳細文件
- 包含常見問題的故障排除

### 維護同步
- 功能變更 → 更新 specification
- 技術決策 → 更新 constitution
- 模組穩定 → 建立或更新 SKILL.md
- **三者保持同步是框架的生命線**
