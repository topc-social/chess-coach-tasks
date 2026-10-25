# How Chess Coach visitors can ask the coach on their own Claude account

Task: topc-social/chess-coach-tasks#7. Written 2026-10-25.

Kamal's rule: the coach runs on each visitor's own Claude, so a question costs the project nothing.

## The options

| Option | What the visitor does | Works for | Cost to the project | Verdict |
|---|---|---|---|---|
| "Sign in with Claude" on our site | Logs in with Claude | n/a | 0 | **Not allowed.** Anthropic says third-party tools should use API keys; subscription use by other apps is only at Anthropic's discretion, billed to usage credits ([Claude help](https://support.claude.com/en/articles/13189465-log-in-to-your-claude-account)). Reported as a ban on third-party subscription auth in Feb 2026 ([AlternativeTo](https://alternativeto.net/news/2026/2/anthropic-officially-bans-using-subscription-authentication-for-third-party-claude-use)). |
| Bring your own API key | Pastes an Anthropic API key | People with a Console account | 0 | Works, but visitors pay per question and most players don't have a key. |
| Chess Coach as an MCP app (connector) | Adds a connector in Claude once | Claude (and ChatGPT) apps | Free-tier server | Best experience: board inside the chat, Claude checks lines live. MCP Apps shipped in Claude in Jan 2026 ([Claude blog](https://claude.com/it/blog/interactive-tools-in-claude), [The Register](https://www.theregister.com/2026/01/26/claude_mcp_apps_arrives)); Claude requires domain signing tied to the server URL ([WorkOS](https://workos.com/blog/2026-01-27-mcp-apps)). Slower to launch. |
| "Ask Claude" button | Clicks, lands in Claude with the question written | Anyone with a Claude account, phone too | 0 | **Recommended for launch.** The page writes the prompt: the board (FEN), side to move, the lesson step, the question, and Stockfish's eval and best lines, so Claude doesn't have to guess. Opens claude.ai with the prompt prefilled where that works; `claude.ai/new?q=` is not documented by Anthropic and reports disagree on whether it still works ([u2l.ai](https://u2l.ai/tools/claude-prompt-link-generator), [GitHub issue](https://github.com/anthropics/claude-code/issues/8827)), so the button also copies the prompt to paste. |

## Recommendation

Launch with the "Ask Claude" button (decided by Kamal, 2026-10-25). Build the MCP app next, once people use the site: it's the only option where Claude can run the engine itself while answering.

Not checked: whether `claude.ai/new?q=` prefills today. Test it in the build; the copy fallback works either way.
