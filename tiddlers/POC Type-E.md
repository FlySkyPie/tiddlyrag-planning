POC Type-D 又稱「TiddlyWeb 調查」，試圖以 PyNest 重新實做 TiddlyWeb，並在完成前中止開發。 

## 說明

綜合 [Type-D](<#POC Type-D>)的發現與結論，轉而研究 TiddlyWeb，並試圖再現其 API 與行為。

重構過程使用乾淨架構：

- Domain
  - 不仰賴函式庫
  - 使用缺血模型模仿 TiddlyWeb 的資料結構
  - 使用 `typing.Protocol` 抽象 TiddlyWeb 的模型方法
- Infrastructure
  - TiddlyWeb 的實作與測試會置於這一層
- Application
  - PyNest 的實作，主要是 HTTP 伺服器一類的邏輯。

如此設計的原因是 TiddlyWeb 的實做缺乏現代開發的邊界感，實作往往有高度的耦合性，很難直接切割，重構策略：

```
Legacy_Model = 缺血模型 + 界面 + Infrastructure 實作
Legacy_Test(Infrastructure 實作)
```

盡可能保持原始的界面，來重複使用單元測試，確保複製原始的業務邏輯。

整個過程會是 Strangler Fig Pattern：

- 大部分實做會置於 Infrastructure 層
- HTTP 相關的落伍實作會由 Application 層取代
- 足夠乾淨的實作會放到 Domain 層

過程中可以慢慢把舊的領域模型與業務邏輯轉譯成現代軟體的建模方式（Service, Repository...）。

## 發現與結論

在 TiddlyWeb 中，關鍵的業務邏輯被分成了三個區塊：

- Filter
- Overlay
- Store

然而這帶來了一個問題，這在現代後端都是需要跟資料庫溝通的行為，通常被抽象化成 Repository。先不談 Overlay 和 Store 在現代架構下可以被合併成一體，問題在於 Filter。

Filter 存在的目的是提供類似 TiddlyWiki 的語法，但是目前實作都是在 Python 內進行的，如果想要保持兼容性，標準的解法是使用 DSL (Domain-specific language) 或 AST (Abstract syntax tree) 作為 Filter 語法和 SQL 的中介層，但是建構並維護這樣一個中介層的成本非常的高。

另外，因為測試案例都是整合測試，因此當軟體結構遷移到現代的抽象方式時(Service, Repository...)，這些測試都變得毫無用處。

簡言之，雖然我成功把核心的業務邏輯以及相關的測試案例重構到現代環境，因為建模的方式依然和現代模型之間存在巨大的鴻溝，實在很難在完整兼容的前提遷移到現代系統。

抽出 OpenAPI 模型，並在理解舊有實作和測試案例的前提下直接重新實作一個部份兼容的 API Server 可能是更好的選擇。

## 程式碼

[https://github.com/FlySkyPie/tiddlyrag-poc/tree/poc/type-e](https://github.com/FlySkyPie/tiddlyrag-poc/tree/poc/type-e)