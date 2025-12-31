# MCP服务器开发工具包 

一个用于使用FastMCP构建模型上下文协议(MCP)服务器并部署到Google Cloud Run的综合指南和模板集合。
A comprehensive guide and template collection for building model Context Protocol (MCP) servers using FastMCP and deploying them to Google Cloud Run.## 工具列表 Tool List

本MCP服务封装下列工具，可让模型通过标准化接口调用以下功能。 本MCP服务封装下列工具，可让模型通过标准化接口调用以下功能。

| 工具 Tool   | 描述 Description         |
|-------|--------------------|
| claude_code | Claude Code Agent: Your versatile multi-modal assistant for code, file, Git, and terminal operations via Claude CLI. Use `workFolder` for contextual execution.  • File ops: Create, read, (fuzzy) edit, move, copy, delete, list files, analyze/ocr images, file content analysis     └─ e.g., "Create /tmp/log.txt with 'system boot'", "Edit main.py to replace 'debug_mode = True' with 'debug_mode = False'", "List files in /src", "Move a specific section somewhere else"  • Code: Generate / analyse / refactor / fix     └─ e.g. "Generate Python to parse CSV→JSON", "Find bugs in my_script.py"  • Git: Stage ▸ commit ▸ push ▸ tag (any workflow)     └─ "Commit '/workspace/src/main.java' with 'feat: user auth' to develop."  • Terminal: Run any CLI cmd or open URLs     └─ "npm run build", "Open https://developer.mozilla.org"  • Web search + summarise content on-the-fly  • Multi-step workflows  (Version bumps, changelog updates, release tagging, etc.)  • GitHub integration  Create PRs, check CI status  • Confused or stuck on an issue? Ask Claude Code for a second opinion, it might surprise you!  **Prompt tips**  1. Be concise, explicit & step-by-step for complex tasks. No need for niceties, this is a tool to get things done. 2. For multi-line text, write it to a temporary file in the project root, use that file, then delete it. 3. If you get a timeout, split the task into smaller steps. 4. **Seeking a second opinion/analysis**: If you're stuck or want advice, you can ask `claude_code` to analyze a problem and suggest solutions. Clearly state in your prompt that you are looking for analysis only and no actual file modifications should be made. 5. If workFolder is set to the project path, there is no need to repeat that path in the prompt and you can use relative paths for files. 6. Claude Code is really good at complex multi-step file operations and refactorings and faster than your native edit features. 7. Combine file operations, README updates, and Git commands in a sequence. 8. Claude can do much more, just ask it!           |


## 检查服务 ## Inspector

工具在线测试： [https://mcp.xiaobenyang.com/inspector/1777316659367939](https://mcp.xiaobenyang.com/inspector/1777316659367939)

Online Tool test [https://mcp.xiaobenyang.com/inspector/1777316659367939](https://mcp.xiaobenyang.com/inspector/1777316659367939)

## 服务配置 MCP Server Config


> #### 如何获取 XBY-APIKEY ？ How to get XBY-APIKEY ?
> 访问小笨羊科技网站 [https://xiaobenyang.com](https://xiaobenyang.com)，注册用户即可获得APIKEY
> Visit XiaoBenYang website [https://xiaobenyang.com](https://xiaobenyang.com), register and get the APIKEY.

### SSE
```json
{
  "mcpServers": {
    "MCP服务器开发工具包": {
      "headers": {
        "XBY-APIKEY": "<YOUR_XBY_APIKEY>"
      },
      "type": "sse",
      "url": "https://mcp.xiaobenyang.com/1777316659367939/sse"
    }
  }
}
```
### STREAMABLE HTTP
```json
{
  "mcpServers": {
    "MCP服务器开发工具包": {
      "headers": {
        "XBY-APIKEY": "<YOUR_XBY_APIKEY>"
      },
      "type": "streamable_http",
      "url": "https://mcp.xiaobenyang.com/1777316659367939/mcp"
    }
  }
}
```
### STDIO
```json
{
    "mcpServers": {
        "MCP服务器开发工具包": {
          "command": "npx",
          "args": [
            "-y",
            "xiaobenyang-mcp"
          ],
          "env": {
            "XBY_APIKEY": "<YOUR_XBY_APIKEY>",
            "mcpId": "1777316659367939",
          },
          "transport": "stdio"
        }
      }
}

```
