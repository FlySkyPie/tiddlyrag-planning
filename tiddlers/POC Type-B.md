POC Type-B 又稱「`AsyncFuncAI/deepwiki-open` 調查」，實作了利用 LLM 對 Git Repo 進行文件摘要的固定 Pipeline。

## 說明

[AsyncFuncAI/deepwiki-open](https://github.com/AsyncFuncAI/deepwiki-open) 是一個實驗性專案，用於將任意 Git Repo 轉換成 4~14 頁不等的文件，用於讓開發者快速理解專案結構與重點，但是程式碼品質極其低下，POC Type-B 僅抽出特定邏輯並實做了其兩階段固定資料流水線：

1. 抽出 Readme 與大約 20 的檔案建立文件大綱。
2. 根據文件大綱，對每一個項目分別生成文件。

## 發現與結論

該 POC 發現了固定流水線的致命缺點，以 `deepwiki-open` 這個庫為例，其包含了 10 種不同語言的 Readme，因此嵌入式檢索會抽出語意完全相同的文件，造成 Pipeline 並無法萃取足夠多樣的資訊。

這的發現隱含了另外一個意義：固定流水線無法適應高度不確定的 Git Repo，因為一個 Git Repo 可能是後端、前端、Monrepo、文件靜態網站產生器...，因此促成了[Type-C](<#POC Type-C>) 的調查。

此外，`deepwiki-open` 本身有高達 16k 的 GitHub 星星數，程式碼卻是由缺乏經驗的前端工程師創造與 Vide Coding 堆疊而成，品質非常惡劣。這對後續田野調查的意義提供一個可靠的先例。

## 程式碼

[https://github.com/FlySkyPie/tiddlyrag-poc/tree/poc/type-b](https://github.com/FlySkyPie/tiddlyrag-poc/tree/poc/type-b)