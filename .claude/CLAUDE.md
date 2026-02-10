# perf-toolkit — AI 協作指令

> 5-15 人 IT 團隊的績效管理工具

## 專案框架

本專案使用 **SDD + Agent Skills** 整合框架：
- **SDD（Spec-Driven Development）**：先定義規格，再驅動實作
- **Agent Skills**：為 AI 提供快速導航入口

## AI 工作流程

### 開始任何任務前，請依序閱讀：

1. **開發憲章** → `.specify/memory/constitution.md`
   - 開發四大原則：工具不做決定、輕量優先、漸進式採用、隱私敏感
   - 技術棧：React/Vue + Python + JSON/CSV
2. **產品規格** → `.specify/memory/specification.md`
   - 四大模組：評估框架、里程碑追蹤、考勤分析、報告產生器
   - 目前在 Phase 1（文件與框架）
3. **對應 Skill** → `.claude/skills/` 下的 SKILL.md
   - `skills/sdd/` — SDD 工作流導航

### 開發規範

- 遵守 constitution.md 中定義的所有原則
- 實作功能前確認 specification.md 中的需求定義
- 變更程式碼後同步更新相關的 spec 文件
- 新增功能模組時，建立對應的 SKILL.md
- 敏感資料（真實姓名、考勤）不進版控

## 目錄結構

```
.claude/skills/     → AI 技能導航（SKILL.md）
.specify/memory/    → 規格文件（constitution + specification）
docs/               → 詳細文檔
src/                → 原始碼（app, components, utils, data）
tests/              → 測試
scripts/            → Python 腳本（考勤分析、報告產生）
templates/          → HTML/Excel 模板
examples/           → 脫敏範例資料
```
