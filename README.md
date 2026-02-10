# perf-toolkit

專為 5-15 人 IT 團隊設計的績效管理工具，從資料收集到報告產出一條龍。

## 解決什麼問題

- 資料散落各處（PPT、HR 系統、主管腦袋裡）
- 評估標準不一致，缺乏結構化框架
- 報告製作耗時，每次重新整理排版
- 歷年無法比較，沒有統一格式

## 核心模組

| 模組 | 功能 | 狀態 |
|------|------|------|
| 評估框架 | 五大面向加權評分 | 規劃中 |
| 里程碑追蹤 | 年度工作計畫與月度進度 | 規劃中 |
| 考勤分析 | HR CSV 匯入與統計分析 | 規劃中 |
| 報告產生器 | 主管版/公佈版/個人版報告 | 規劃中 |

## 專案結構

```
perf-toolkit/
├── .claude/                    ← AI 協作設定
│   ├── CLAUDE.md               ← 專案級 AI 指令
│   └── skills/sdd/SKILL.md    ← SDD 工作流導航
├── .specify/memory/            ← 規格驅動開發
│   ├── constitution.md         ← 開發憲章
│   └── specification.md        ← 產品規格
├── docs/                       ← 文檔
├── src/                        ← 原始碼
├── tests/                      ← 測試
├── scripts/                    ← Python 腳本
├── templates/                  ← 報告/Excel 模板
└── examples/                   ← 範例資料
```

## 開發方法論

本專案使用 **SDD + Agent Skills** 整合框架：

- **SDD（Spec-Driven Development）**：先寫規格再開發，所有實作有依據
- **Agent Skills**：為 AI 助手提供快速導航，提升協作效率

詳見 [框架使用指南](docs/guide.md)。

## 設計原則

1. **工具不做決定** — 系統提供數據與參考，最終判斷是主管的
2. **輕量優先** — JSON/CSV 存資料，零部署成本
3. **漸進式採用** — 各模組獨立可用，不需全套導入
4. **隱私敏感** — 預設脫敏，敏感資料不進版控

## 開發階段

- **Phase 1**：文件與框架（當前）
- **Phase 2**：報告產生器
- **Phase 3**：Web 應用
- **Phase 4**：AI 協作增強

## License

MIT
