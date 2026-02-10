# 發佈機制

## 架構

```
push to main ──→ GitHub Actions ──→ GitHub Pages
                  (自動觸發)          (靜態站台)
```

## 站台網址

- 首頁：https://joechiboo.github.io/perf-toolkit/
- 範例報告：https://joechiboo.github.io/perf-toolkit/examples/report-manager-sample.html

## 運作方式

### 自動部署

每次 push 到 `main` 分支，GitHub Actions 會自動：

1. Checkout 程式碼
2. 將整個 repo 打包為靜態資源
3. 部署到 GitHub Pages

Workflow 定義在 `.github/workflows/pages.yml`。

### 什麼會被發佈

根目錄下的所有檔案都會上到 Pages，包含：

- `index.html` — 首頁索引
- `examples/` — 脫敏範例報告
- `docs/` — 文檔（Markdown 不會被渲染，需用 HTML 瀏覽）

### 什麼不會被發佈

被 `.gitignore` 擋掉的檔案不會進 repo，自然不會被發佈：

- `*績效評估報告*` — 含真實個資的報告
- `*考勤*raw*` — 原始考勤資料
- `.env` — 環境變數

## 新增頁面

### 新增報告範例

1. 建立脫敏後的 HTML 檔案到 `examples/`
2. 在 `index.html` 加上連結
3. Push 到 main，自動部署

```html
<!-- 在 index.html 中新增 card -->
<div class="card">
  <h3><a href="examples/新檔案.html">標題</a><span class="badge">範例</span></h3>
  <p>說明文字</p>
</div>
```

### 新增文檔頁面

如果需要讓 Markdown 文檔也能在 Pages 上好看地呈現，未來可考慮：

- 加入 Jekyll（GitHub Pages 原生支援）
- 或用簡單的 HTML 包裝

目前 Phase 1 暫不需要，直接用 HTML 即可。

## 監控部署

### 查看部署狀態

```bash
# 最近一次 Actions 執行
gh run list --limit 1

# 查看詳細 log
gh run view <run-id>
```

### 部署失敗排查

常見原因：

- **權限問題**：確認 repo Settings > Pages 設為 GitHub Actions
- **Workflow 語法錯誤**：檢查 `.github/workflows/pages.yml`
- **檔案太大**：GitHub Pages 有 1GB 限制

## 注意事項

- 此站台為 **public**，任何人都能存取
- 確保所有上傳的 HTML 都已完成脫敏
- 不要在 HTML 中放入真實姓名、考勤原始數據等敏感資訊
- 範例資料一律使用代號（PG-01, MIS-01, IF-01 等）
