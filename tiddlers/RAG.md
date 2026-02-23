檢索增強生成 (RAG, Retrieval-augmented generation) 是一種使大語言模型（LLM）能夠從外部資料來源中檢索並整合新資訊的技術。

![](#simple-rag.webp)

RAG 系統主要包含幾個步驟與組件，知識準備階段：

- 原始資料
  - 可能是 Word 檔、PDF、HTML...必須轉換成純文本格式，例如 Markdown 或 txt。
- 切塊 (Chunking)
  - 對原始資料進行切塊，通俗的講就是根據段落將單一文件拆分成多個文本。
- 嵌入
  - 對每一個資訊塊進行嵌入 (Embedding)，意思是透過某種演算法將文字塊轉換成一個高維度的語意向量。
  - 轉換的分式因演算法而異，目前主流使用基於 [Transformer](https://en.wikipedia.org/wiki/Transformer_(deep_learning)) 的類神經模型來完成該任務。
- 匯入向量資料庫
  - 向量資料庫是一種以向量為索引機制的資料庫，將資訊塊與嵌入向量寫入資料庫後，便可用向量來索引資料。

知識使用（檢索）階段：

- 嵌入
  - 將使用者的問題或請求進行嵌入。
- 檢索
  - 透過請求的嵌入向量檢索數個資訊塊。
- 提示詞填充 (Prompt Stuffing)
  - 將資訊塊填入 LLM 的上下文之中，來取得更可靠的輸出結果。
