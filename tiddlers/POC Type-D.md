POC Type-D 又稱「MWS 調查」，試圖以 NestJS 重新實做 MWS (MultiWikiServer)，並在完成前中止開發。

## 說明

在 [Type-B](<#POC Type-B>) 與 [Typ-C](<#POC Type-C>) 中引入了 Gitea 實例作為 Git Repo 的微服務，而在 [Type-A](<#POC Type-A>) 中雖然可以匯入和匯出 TiddlyWiki，但是匯入狀態的 TiddlyWiki 只能透過 API 讀取，缺乏 GUI 與之互動，但是寫一個獨立的 GUI 又會破壞 TiddlyWiki 的意義。

綜合上述，應該要有一個「能以微服務儲存 TiddlyWiki 同時滿足人類瀏覽或操作」的實例作為通用域解決方案。

## 發現與結論

過程中建立了[TiddlyWiki 資料庫方案與生態](<#TiddlyWiki 資料庫方案與生態>)的領域知識。

為了 MWS 專案中 Issue 的討論情況，根據 [ETL](#ETL)/Data Orchestration 框架建立了工具用來快速翻譯 Git Issue，翻譯完成後得到以下結論：

- AuthZ 方案選擇使用 ACL，大部分的 Issue 都在繞著 ACL 相關的問題討論。
  - 然而 MWS 的資料模型是建立在 Recipe-Bag 多對多關係下，ReBAC 才是合適的 ACM。換句話說，這個專案正在經歷錯誤的技術決策造成的泥沼。
- 關於 Admin UI 的討論則是第二多的討論。
  - 然而此時 MWS 的核心運作依然不穩定，並沒有提供方便 DevOps 快速搭建服務的選項（如：預建置 OCI 映像檔）。
  - 其中甚至涉及透過 RPC 實現前後端混合渲染之類的話題。（基本上重新發明 Nest.js）
- 程式碼風格延續 TiddlyWiki 時期的邊界模糊。
  - 可靠性堪憂。
  - 安全性堪憂。
  - 「社群自 high 專案」，無法吸引使用主流技術棧的開發者。
  - 大量的「重複輪子」程式碼。
- 主要開發者 Arlen22 認為「Docker 對使用者不友善」。

就算不考慮實作，MWS 的 API 設計也十分臃腫，充滿了錯誤的 ACL 、 RPC (Remote Procedure Call) 和 SSE (Server-Sent Events)。

TiddlyWeb 的程式碼大小大約為 600 KiB， MWS 則是 2 MiB，因此如果要抄 API 界面，TiddlyWeb 可能還比較合適，它甚至有寫測試案例。

## 程式碼

中止的 POC 本題：

[https://github.com/FlySkyPie/tiddlyrag-poc/tree/poc/type-d](https://github.com/FlySkyPie/tiddlyrag-poc/tree/poc/type-d)

[ETL](#ETL) 副產物：

[https://github.com/FlySkyPie/github-issue-simple-etl](https://github.com/FlySkyPie/github-issue-simple-etl)