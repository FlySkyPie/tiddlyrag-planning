BEIR (Benchmarking Information Retrieval) 基準測試是一個標準化框架，旨在評估搜尋與檢索演算法在不同任務和數據集上的有效性。它提供了一系列數據集，每個數據集代表不同類型的資訊檢索場景，例如問答 (question answering)、事實核查 (fact verification) 或文件搜尋 (document search)。BEIR 的主要目標是衡量檢索模型對於未經明確訓練之任務的泛化能力，這對於評估實際應用性至關重要。開發者與研究人員利用 BEIR，透過在同一組任務上進行測試來公平地比較模型，確保研究結果具有可重現性且各研究間具備可比性。

使用 BEIR 的方式是將檢索模型運行於其套件中的數據集，並使用 nDCG (normalized Discounted Cumulative Gain)、recall@k 或 MAP (Mean Average Precision) 等指標來衡量性能。例如，開發者可能會在 BEIR 的數據集上，針對傳統的關鍵字模型 BM25 測試 Sentence-BERT 等密集檢索模型 (dense retrieval model)。BEIR 中的每個數據集都包含查詢 (queries)、相關文件以及預定義的訓練/測試分割，允許模型在零樣本 (zero-shot) 設定下進行評估——這意味著模型不會針對受測的特定數據集進行微調 (fine-tuned)。這種設置模擬了現實世界的場景，即模型必須在未見過的數據上表現良好。透過彙整各數據集的結果，BEIR 提供了模型優缺點的全方位視角，例如模型在處理專業術語（如科學論文中）或對話式查詢方面的表現是否較佳。

BEIR 的核心特色在於其多樣性。例如，它包含如 BioASQ (biomedical question answering)、TREC-COVID (scientific search during the pandemic) 以及 HotpotQA (multi-hop reasoning) 等數據集。每個數據集都以獨特的方式挑戰模型：BioASQ 測試特定領域的知識，而 HotpotQA 則需要跨多個文件連接資訊。開發者可以利用這些基準測試來識別模型的差距——例如，某個檢索器可能在 FEVER 的事實核查任務中表現掙扎，但在 MS MARCO 的一般網頁搜尋中表現優異。透過分析性能差異，團隊可以優先處理改進事項，例如增強模型處理否定詞或長尾查詢 (long-tail queries) 的能力。BEIR 的標準化評估流程也減少了建立自定義基準測試的開銷，讓開發者能專注於模型優化而非數據準備。

程式碼：

- [https://github.com/beir-cellar/beir](https://github.com/beir-cellar/beir)
  - 2.1k ⭐