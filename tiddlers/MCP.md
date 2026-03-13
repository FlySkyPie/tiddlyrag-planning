MCP (Model Context Protocol) 是一種設計給 [LLM](#LLM) 使用的通訊協定，有幾種型態：

- STDIO ([MCP over stdio](<#MCP over STDIO>))
- HTTP SSE ([MCP over SSE](<#MCP over SSE>))
- Streamable HTTP ([MCP over Streamable HTTP](<#MCP over Streamable HTTP>))

MCP 的流程包含：

1. [交握](<#MCP 交握>)
2. [問答](<#MCP 問答>)

流程內的資料包含三大類：

- [Request](<#MCP Request>)
- [Response](<#MCP Response>)
- [Notifications](<#MCP Notifications>)

---

MCP 的規格書以[官方的文件](<#MCP 官方規格書>)為準，本文件的資訊僅供參考。