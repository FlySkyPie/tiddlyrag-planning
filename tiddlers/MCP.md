MCP (Model Context Protocol) 是一種設計給 [LLM](#LLM) 使用的通訊協定，有兩種型態：

- stdio ([MCP over stdio](<#MCP over stdio>))
- HTTP ([MCP over HTTP](<#MCP over HTTP>))

MCP 的流程包含：

1. [交握](<#MCP 交握>)
2. [問答](<#MCP 問答>)

流程內的資料包含三大類：

- [Request](<#MCP Request>)
- [Response](<#MCP Response>)
- [Notifications](<#MCP Notifications>)

---

MCP 的規格書以[官方的文件](<#MCP 官方規格書>)為準，本文件的資訊僅供參考。