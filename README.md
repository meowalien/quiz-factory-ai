# Quiz Factory

Create practice question banks from any topic, notes or document right in your chat, then drill them on the web, share them with people you invite, or publish them.

Your AI assistant writes the questions; Quiz Factory saves them as a practice bank on [quiz-factory.tw](https://quiz-factory.tw) that you can drill again and again, share with people you invite, or publish.

This repository holds the plugin files for Claude and Codex: one skill and the connection settings for a remote MCP server.

```
https://mcp.quiz-factory.tw/mcp
```

## Install

**Claude Code**

```
/plugin marketplace add meowalien/quiz-factory-ai
/plugin install quiz-factory@quiz-factory
```

**Codex**

```
codex plugin marketplace add meowalien/quiz-factory-ai
```

Then run `/plugins` inside Codex to install `quiz-factory`, and `codex mcp login quiz-factory`.

**Other assistants** (ChatGPT, claude.ai, Cursor, VS Code, Gemini CLI, Grok and more): add a remote MCP server with the URL above. Step-by-step instructions for each assistant: <https://quiz-factory.tw/en/ai>

The first time a tool runs, you sign in to your Quiz Factory account and approve access. You can remove the connection at any time in your account menu on quiz-factory.tw.

## Try it

- "Make a 10-question quiz on high school English vocabulary"
- "Put this bank online"
- "Are there any public banks or past exam papers on organic chemistry?"

## What is in this plugin

- `skills/build-quiz-bank/SKILL.md`: tells the assistant when to save questions to Quiz Factory and how to use the tools. It runs no code.
- `.mcp.json`: the address of the remote MCP server. No headers, no credentials.

The tools the server offers:

| Tool | What it does |
|---|---|
| `get_authoring_guide` | Returns the question format and your account's limits |
| `create_bank`, `update_bank_info` | Create a bank, change its name or description |
| `add_questions`, `update_question`, `delete_question`, `reorder_questions`, `move_question`, `set_chapters` | Write, edit and organise questions |
| `update_passage` | Edit a shared passage (an article, chart or case used by several questions) |
| `request_image_upload`, `confirm_image_upload` | Attach a picture to a question |
| `list_my_banks`, `get_bank` | Read your banks |
| `publish_bank`, `unpublish_bank` | Put a bank online (public or invite-only), or take it offline |
| `request_bank_deletion`, `delete_bank` | Delete a bank; the assistant must ask you first |
| `search_public_banks` | Search public banks and past exam papers |

## Data handling

- **Where it connects**: only `https://mcp.quiz-factory.tw/mcp`, operated by Quiz Factory. Sign-in uses OAuth on quiz-factory.tw.
- **What is sent**: the arguments of each tool call, that is, the bank's name and description, the questions, answers and explanations the assistant wrote, and any picture you ask it to upload. The plugin does not read your chat history, memory or other files.
- **Where it is stored**: in your Quiz Factory account. Drafts are visible only to you. Public banks are reviewed by the site before they appear in search; invite-only banks are visible to the people you invite.
- **How long it is kept and how to delete it**: drafts are temporary and a draft left unchanged for a while is deleted automatically; a bank that is online is kept until you delete it or delete your account. You can delete a bank from the assistant or on the site. The full rules are in the [Terms of Service](https://quiz-factory.tw/en/terms) and the [Privacy Policy](https://quiz-factory.tw/en/privacy).
- **Training**: your content is not used to train models.

## Help

Troubleshooting and contact: <https://quiz-factory.tw/en/ai/help> · service@quiz-factory.tw

## License

MIT
