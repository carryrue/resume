# 履歷型 Portfolio 網站 Spec
## Apple Liquid Glass 升級版

## 目的
建立一個單頁式個人履歷 / portfolio 網站，採用**真正的 Apple Liquid Glass 風格**，適合 GitHub Pages 發佈。

## 技術要求
- 單一檔案：`index.html`
- CSS 內嵌在 `<style>` 內（**只修改 style 區塊，不重寫 HTML**）
- 不使用 React / Vue / 任何打包工具
- 手機與桌面皆適配
- 在 Safari / Chrome / iOS 瀏覽器上具有流暢的玻璃質感
- 參考：macOS Big Sur 設定面板、iOS Control Center

---

## 🎨 視覺設計規範

### 1️⃣ **背景系統**
- **雙層 radial-gradient 光暈**
  - 第一層：深藍（#08101f） → 紫粉（rgba(156, 106, 255, ...)）
  - 第二層：深藍 → 青色（rgba(47, 198, 255, ...)）
- **慢慢飄動效果**
  - CSS `@keyframes` 動畫（8-12 秒循環）
  - 使用 `transform: translate()` 輕微位移漸層背景
  - 優先使用 `background-position` 動畫或偽元素位移

### 2️⃣ **玻璃卡片 (Glass Card)**
```css
/* 核心玻璃特性 */
backdrop-filter: blur(24px);
background: rgba(255,255,255,0.12);  /* 半透明白底 */
border: 1px solid rgba(255,255,255,0.22);  /* 1px 半透明白邊 */
border-radius: 28px;
```
- **頂部高光層**：`linear-gradient(180deg, rgba(255,255,255,0.10), transparent 50%)`
- **陰影**：`0 30px 80px rgba(0,0,0,0.24)`

### 3️⃣ **互動效果 - Hover 卡片**
- **柔光浮起**：
  - `transform: translateY(-2px)` 微微上升
  - 陰影加深：`0 34px 90px rgba(0,0,0,0.28)`
  - 過渡時間：0.25s cubic-bezier 曲線
- **背景亮度微增**（可選）：`background: rgba(255,255,255,0.14)`

### 4️⃣ **Timeline 樣式**
- **左邊垂直軸**：1px 半透明白線 `rgba(255,255,255,0.18)`
- **時間點圓點**：
  - 直徑 12px
  - 背景：藍紫漸層
  - 邊框：1px 半透明白邊
- **發光效果**：
  - Box-shadow：`0 0 12px rgba(159,140,255,0.4)`
  - 可加 `:hover` 時亮度增加

### 5️⃣ **Tag 雲（膠囊狀）**
```css
border-radius: 999px;  /* 完全圓角 */
padding: 10px 16px;
background: rgba(255,255,255,0.08);
border: 1px solid rgba(255,255,255,0.18);
```
- **對比邊框**：在暗色背景上凸顯清晰度
- **Hover 效果**：背景微亮 + 邊框色增強
- **尺寸**：小號標籤適用

### 6️⃣ **文字對比度**
- **主文字**：#f2f7ff (95+ WCAG contrast)
- **副文字**：rgba(242,247,255,0.78) (80+ WCAG contrast)
- **標題**：#c7cbff (確保在玻璃上可讀)
- **強調色**：#9f8cff (紫色，視覺亮點)

---

## 區塊架構（依序）

1. Hero
   - 頭像：圓角漸層背景，有光澤高光
   - 大名：超大粗體標題
   - 一句話職涯定位：軟文本顏色
   - 求職方向 pills：膠囊標籤

2. About 關於我
   - 白玻璃卡片容器
   - 2-3 段自介文字
   - 標籤：求職方向 / 所在地 / 語言（膠囊 pill）

3. Skills 核心技能
   - 每組分類獨立玻璃卡片
   - Tag 雲排列（膠囊狀、半透明邊框）

4. Education 學歷 ⏳
   - Timeline 左軸視覺化
   - 圓點 + 發光效果
   - 時間 | 校名 | 系所

5. Experience 經歷 ⏳
   - Timeline 左軸視覺化（同上）
   - 公司 | 職位 | 時間
   - 數字化成果（加粗或強調色）

6. Awards 競賽獎項
   - 玻璃卡片 grid 排列
   - 包含 emoji badge
   - 獲獎時間 + 獎項名

7. Projects 作品集
   - 玻璃卡片 grid 排列
   - 專案圖示 / 標題 / 簡述
   - 技術 tag

8. Contact 聯絡
   - 4 顆按鈕：Email / GitHub / LinkedIn / IG
   - 按鈕樣式：玻璃 pill 按鈕，hover 時背景亮化

## 導覽功能
- 頁面頂部浮動 TOC 導覽列（玻璃卡片樣式）
- 7 個錨點：關於 / 技能 / 學歷 / 經歷 / 獎項 / 作品 / 聯絡
- sticky 固定在頁面頂端 (z-index: 20)
- 手機版可橫向滾動
- 點擊後平滑捲動 (scroll-behavior: smooth)

## 可替換內容
- 名稱：王小明
- 學校：中原大學 資管系
- 目標職務：AI 工程師
- 公司類型：FinTech / 顧問業 / 科技業
- 各區塊範例文字可後續直接替換

## 實作規則
1. **只修改 `<style>` 區塊**，不重寫 HTML
2. 實作時僅限 HTML / CSS，不額外加入 JavaScript 框架
3. 所有互動效果均以純 CSS 為主
4. 使用原生瀏覽器 `scroll-behavior: smooth` 實現平滑捲動
5. 使用 `@keyframes` 實現背景飄動動畫

---

## ✅ 設計驗收清單

- [ ] 背景雙層漸層 + 慢速飄動
- [ ] 玻璃卡片 (blur 24px + 半透明白底 + 白邊)
- [ ] 卡片 hover 有柔光浮起 (translateY -2px)
- [ ] Timeline 左軸 + 圓點 + 發光
- [ ] Tag 雲膠囊狀 + 對比邊框
- [ ] 文字對比度 ≥ 80 WCAG
- [ ] 導覽列 sticky + 可滾動
- [ ] 手機適配 ✅
