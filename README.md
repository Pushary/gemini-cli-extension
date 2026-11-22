# Pushary for Gemini CLI

Answer Gemini CLI from your phone, and get a push when a long task finishes or fails.

## What it does

Gemini CLI keeps working after you walk away from the terminal. Pushary reaches you on your phone or Mac, in the same inbox as your other AI agents such as Claude Code, Codex and Cursor.

1. **Ask.** When Gemini needs a decision only you can make, it asks you through Pushary: yes or no, a choice of options, or a short answer. You answer from the Pushary phone or Mac app, and Gemini carries on.
2. **Notify.** When a long task finishes, or fails in a way Gemini cannot fix, Gemini sends you a push with the result.
3. **Remind.** Gemini can set a one-time personal reminder that Pushary delivers later.

## What is in this extension

| Component | File | What it does |
| --- | --- | --- |
| MCP server | `gemini-extension.json` | Connects Gemini CLI to Pushary's hosted MCP server at `https://pushary.com/api/mcp/mcp` |
| Context | `GEMINI.md` | A short rule for when to ask and when to notify |
| Skill | `skills/pushary/SKILL.md` | Instructions for when to ask, when to notify and how to wait for an answer |

The extension adds no hooks, commands, scripts or dependencies.

## What connecting does

- **Network endpoints.** Gemini CLI calls `https://pushary.com/api/mcp/mcp` for the Pushary tools, and `https://clerk.pushary.com` once, to sign you in.
- **Credentials.** You sign in with your Pushary account over OAuth in your browser. There is no API key to paste.
- **What Gemini sends.** Only what it puts in a Pushary tool call: the question or notification text, optional detail such as a summary or an error message, the agent name and a session id. Pushary stores these so they show in your inbox and history.
- **What Pushary does not see.** Your Gemini sessions, your files and your other tools, apart from what Gemini puts in a tool call.

Read the [privacy policy](https://pushary.com/privacy) for retention details.

## What you need

- A paid Pushary plan for your own agents, such as Agent, Agent Pro or Team. Eligible web sign-ups get a trial; see [pricing](https://pushary.com/pricing).
- The Pushary app on your phone, or the Pushary Mac app, signed in to the same account. Get them at [pushary.com/download](https://pushary.com/download).

## Install

```bash
gemini extensions install https://github.com/Pushary/gemini-cli-extension
```

Start Gemini CLI and run `/mcp auth pushary`. Sign in with your Pushary account in the browser and allow access.

Then check that a question reaches you. Ask Gemini:

```text
Use Pushary to ask me "Did this reach you?" as a yes or no question, with agentName "Gemini CLI - Setup check". Wait for my answer and tell me what I chose.
```

Answer on your phone. Gemini should tell you your answer.

## Approve tool calls from your phone

This extension lets Gemini ask you. It does not stop Gemini from running a command. To approve shell commands and edits from your phone before they run, install Pushary's hooks with the Pushary command line:

```bash
npx -y pushary@latest setup
```

Read the [Gemini CLI guide](https://pushary.com/docs/agents/guides/gemini-cli) before you run it.

## What it does not do

- It does not gate Gemini's tool calls on its own. Gemini's approval mode and policies still decide what runs. Use the hooks above for phone approvals.
- A question asked through this sign-in closes 10 minutes after it is sent. A question that closes unanswered is never treated as a yes.
- Gemini decides when to call Pushary. The skill guides it; nothing forces it.

## Support

- Guide: [pushary.com/docs/agents/guides/gemini-cli](https://pushary.com/docs/agents/guides/gemini-cli)
- Help: [pushary.com/support](https://pushary.com/support)

## License

MIT. See [LICENSE](LICENSE).
