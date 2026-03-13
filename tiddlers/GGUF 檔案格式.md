GGUF (Georgi Gerganov Machine Learning Tensor library) 是一種用於儲存模型的檔案格式，這些模型將用於 [GGML](<#GGML 函式庫>) 推理以及基於 [GGML](<#GGML 函式庫>) 的執行器。 GGUF 是一種二進位格式，旨在實現模型的快速載入和保存，並便於讀取。傳統上，模型使用 PyTorch 或其他框架開發，然後轉換為 GGUF 格式以便在 GGML 中使用。

GGUF 是 [GGML](<#GGML 檔案格式>)、GGMF 和 GGJT 的後繼檔案格式，其設計旨在確保模型的明確性，因為它包含了載入模型所需的所有資訊。此外，GGUF 還具有可擴展性，因此可以在不破壞相容性的情況下為模型添加新資訊。