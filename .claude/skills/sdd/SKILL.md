# SDD 工作流 — Spec-Driven Development

## 概述
此技能引導 AI 執行規格驅動開發流程：先讀規格、再做實作、最後同步文檔。

## 核心文件
- [開發憲章](../../../.specify/memory/constitution.md) - 開發原則與技術限制
- [產品規格](../../../.specify/memory/specification.md) - 功能需求與使用者故事
- [框架指南](../../../docs/guide.md) - 完整使用說明

## 工作流程

```
┌─────────────────────────────────────────────┐
│              SDD + Skills 工作流              │
├─────────────────────────────────────────────┤
│                                             │
│  1. 讀取規格                                 │
│     ├── constitution.md  → 了解原則          │
│     └── specification.md → 了解需求          │
│                                             │
│  2. 確認範圍                                 │
│     ├── 對應哪個功能模組？                    │
│     ├── 在哪個實作階段？                      │
│     └── 有無相關的 SKILL.md？                │
│                                             │
│  3. 實作                                     │
│     ├── 遵守 constitution 原則               │
│     ├── 滿足 specification 需求              │
│     └── 程式碼放 src/，測試放 tests/          │
│                                             │
│  4. 同步文檔                                 │
│     ├── 更新 specification 的完成狀態         │
│     ├── 必要時更新 constitution              │
│     └── 必要時新增/更新 SKILL.md             │
│                                             │
└─────────────────────────────────────────────┘
```

## 常用操作

### 新功能開發
1. 閱讀 `specification.md` 找到對應需求
2. 確認 `constitution.md` 中的技術限制
3. 在 `src/` 中實作
4. 在 `tests/` 中測試
5. 更新 specification 中的 checkbox

### 新增 Skill
```bash
mkdir -p .claude/skills/[skill-name]
# 建立 SKILL.md，參考本檔案格式
```

### 更新規格
- 功能需求變更 → 更新 `specification.md`
- 技術決策變更 → 更新 `constitution.md`
- 兩者需保持同步

## 故障排除

### 問題：不確定該改哪個 spec 文件
- **原因**：constitution 管「怎麼做」，specification 管「做什麼」
- **解法**：
  - 改開發原則/技術限制 → `constitution.md`
  - 改功能需求/使用者故事 → `specification.md`

### 問題：SKILL.md 路徑連結失效
- **原因**：相對路徑層級不對
- **解法**：從 `.claude/skills/[name]/` 到專案根目錄需要 `../../../`
