# Connect MCP — Notes

---

## Screenshot & Video Plan

| # | Type | Description | Why it belongs here |
|---|------|-------------|---------------------|
| 1 | Screenshot | Willow sidebar with "Connect MCP" highlighted | Users need to find the entry point. The sidebar isn't immediately obvious to a first-timer. |
| 2 | Screenshot | The full Connect MCP dialog | This is the key UI moment — show the user exactly what they'll see before they see it. |
| 3 | Screenshot | Cursor MCP settings panel with Willow listed | Confirms what success looks like after the Cursor manual setup. |
| 4 | Screenshot | Claude Desktop chat with a tool call inline | Shows the user what a connected state looks like. |
| 5 | Video | 30s end-to-end: Cursor → type prompt → tool fires → result returned | Answers "will this actually work?" before the user tries it. No narration; a title card does the work. |

If only one visual gets captured first, make it Screenshot #2 (the Connect MCP dialog) — it's the UI element the entire page is built around.

---

## Accuracy Pass

Claims and steps that couldn't be fully verified from outside the product. Each needs a check before the page ships.

**1. Authentication model — high priority**
The docs show no auth headers in any JSON config example. For MCP over HTTP, clients typically need a bearer token or API key in the request headers. If Willow handles auth differently (e.g., a browser-based SSO flow, a session-scoped URL, or a token embedded in the URL itself), the page needs to explain that. If headers *are* required, every config example is wrong.
*Check:* Connect a client manually and inspect the network requests, or confirm with engineering.

**2. `<server-name>` slug values**
The page uses `github` as the example slug. Confirm the actual slug format — is it case-sensitive? Is it always the lowercase service name, or does it vary?
*Check:* Inspect the MCP Servers page server cards for the slug field, or test the URL with a known server.

**3. Claude Desktop: Streamable HTTP support**
Older versions of Claude Desktop (pre-0.10) only support stdio-based MCP servers, not HTTP. Users on older versions will get a silent failure.
*Check:* Minimum Claude Desktop version that supports `url:` in `mcpServers`.

**4. Claude Code: `--transport http` flag**
The exact syntax may use `--transport streamable-http` rather than `http` depending on Claude Code version.
*Check:* Run `claude mcp add --help` in a current Claude Code install.

**5. VS Code: JSON schema for MCP servers**
The `type: "http"` key in `.vscode/mcp.json` may have changed — the Copilot Chat extension schema evolves. Current schema may use `transport` or `protocol` instead.
*Check:* VS Code Copilot Chat extension changelog or the `mcp.json` schema reference.

**6. Windsurf: Settings UI location**
The Windsurf steps are inferred — couldn't verify the exact location of MCP settings in the current UI.
*Check:* Open Windsurf and confirm the Settings → MCP Servers path, or check Windsurf's own MCP docs.

**7. "Internal AI Chat" — definition unclear**
The rewrite assumes this is Willow's own built-in chat. If it refers to something else (a white-labeled product, a different feature), the section needs different content.
*Check:* Clarify with the product team.

**8. Dynamic MCP Gateway auth**
The rewrite treats the DMCP URL identically to the standard Gateway. If it has different authentication requirements or a separate setup step, a note is needed.

---

## Editorial Note

**What's wrong with the current page**

The current page was written to document the feature, not to help someone use it. It reads like a feature spec — "the dialog offers automated configuration buttons for Cursor and VS Code" — rather than instructions. It never tells the reader what to do first, what to copy, or what success looks like. The structure mirrors the UI elements instead of following the user's mental journey: find the dialog → get a URL → configure my client → verify it works. The tone is passive and institutional. Nothing in it sounds like it was written by someone who has actually tried to connect Cursor to an MCP server at midnight when it's not working.

**What I changed and why**

I restructured around the user's task, not the feature's shape. The four-step flow (open dialog → choose URL → configure client → verify) matches exactly what a user needs to do, in order. I added a "Before you start" check so users don't get halfway through setup before discovering they have no servers enabled. I explained the `<org>` and `<server-name>` placeholders explicitly — the current page leaves those as mystery values without telling you where to find them, which is the most common point of failure. I added a "Verify it's working" section because new users often don't know whether they've connected correctly until they see a tool call fire.

**What I'd do to the docs as a whole**

The docs split information across pages in a way that doesn't map to user tasks. A first-time user has to visit Intro → MCP Servers → Connect MCP in sequence to understand what's happening, but there's no explicit path connecting them. I'd add a short "First 10 minutes" guide on the Intro page that links these steps explicitly. Every page also needs an "is this working?" section — the troubleshooting information is currently buried on the Intro page, which is the last place someone goes when something breaks. And the placeholder values (`<org>`, `<MCP_NAME>`) should be auto-populated from the user's session on the live docs site — the user shouldn't have to know their org slug; Willow already does.
