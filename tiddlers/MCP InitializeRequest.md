```typescript
{
  jsonrpc: "2.0",
  id: number | string,
  method: "initialize",
  params?: {
    protocolVersion: string;
    capabilities: ClientCapabilities;
    clientInfo: Implementation;
  }
}
```

繼承 [Request](<#MCP Request>)。

---

[MCP](<#MCP>) 的規格書以[官方的文件](<#MCP 官方規格書>)為準，本文件的資訊僅供參考。