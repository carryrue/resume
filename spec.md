# 履歷型 Portfolio 網站 Spec

## 目的
建立一個單頁式個人履歷 / portfolio 網站，採用 Apple Liquid Glass 風格，適合 GitHub Pages 發佈。

## 技術要求
- 單一檔案：`index.html`
- CSS 內嵌在 `<style>` 內
- 不使用 React / Vue / 任何打包工具
- 手機與桌面皆適配
- 在 Safari / Chrome / iOS 瀏覽器上具有流暢的玻璃質感

## 設計風格
- 背景：深藍到紫粉的雙層 `radial-gradient` 漸層光暈
- Glass 卡片：`backdrop-filter: blur(24px)`、半透明白底、1px 半透明白邊
- hover 卡片：柔光浮起效果
- 文字清晰可讀，保留足夠對比度
- 整體感受：類似 macOS Big Sur 設定面板、iOS Control Center

## 區塊架構（依序）
1. Hero
   - 頭像
   - 大名
   - 一句話職涯定位
   - 求職方向 pills
2. About 關於我
   - 2-3 段自介
   - 求職方向 / 所在地 / 語言 標籤
3. Skills 核心技能
   - 多組分類
   - 每組 tag 雲
4. Education 學歷
   - timeline 樣式
5. Experience 經歷
   - timeline 樣式
   - 含數字化成果
6. Awards 競賽獎項
   - 卡片 grid
   - 包含 emoji badge
7. Projects 作品集
   - 卡片 grid
8. Contact 聯絡
   - 4 顆按鈕：Email / GitHub / LinkedIn / IG

## 導覽功能
- 頁面頂部加浮動 TOC 導覽列
- 7 個錨點：關於 / 技能 / 學歷 / 經歷 / 獎項 / 作品 / 聯絡
- sticky 固定在頁面頂端
- 手機版可橫向滾動
- 點擊後平滑捲動

## 可替換內容
- 名稱：王小明
- 學校：中原大學 資管系
- 目標職務：AI 工程師
- 公司類型：FinTech / 顧問業 / 科技業
- 各區塊範例文字可後續直接替換

## 補充說明
- 先完成 `spec.md` 確認後，再產生 `index.html`
- 實作時僅限 HTML / CSS，不額外加入 JavaScript 以外部框架
- 所有互動效果均以純 CSS 為主，若需 smooth scroll 會使用原生瀏覽器支援
