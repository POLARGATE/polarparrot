# PolarParrot

Mac app that records your meetings without adding a bot, writes the notes, and lets your AI read them.

Website: https://polarparrot.com. Made by [Polargate](https://polargate.ai). The app is closed source. This repository holds the public guides and configuration.

## What it does

- Records your Mac's audio and your microphone when you press record, on two separate tracks.
- Writes notes with a summary, decisions, actions and questions.
- Lets Claude, ChatGPT, Cursor and Claude Code read those notes through an MCP connector. Read-only.
- Saves each note as Markdown in a folder you pick.

macOS only. FaceTime can't be recorded: macOS only lets the app record your voice there. On Teams calls with three or more people there is an open bug, and the app warns you if the others stop being heard.

Always tell the people in a meeting that you are recording.

## Connect your AI

The connector address is:

```
https://polarparrot.com/mcp
```

It uses OAuth with your PolarParrot account. Sign in with your email and a code. If you signed in to the app with Apple or Google, open Connect your AI in the app and click Show my code.

### Claude

Customize > Connectors > + Add > Add custom connector. Paste the address, click Add, then Connect.

### Claude Code

```bash
claude mcp add --transport http polarparrot https://polarparrot.com/mcp
```

Then open Claude Code, type `/mcp` and sign in.

### Cursor

Add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "polarparrot": { "url": "https://polarparrot.com/mcp" }
  }
}
```

### ChatGPT

In ChatGPT's settings, under Connectors, create a new one and paste the address. You need a ChatGPT plan that allows custom connectors.

## Tools

| Tool | What it does |
|---|---|
| `buscar_reuniones` | Searches by words, dates or person |
| `acta` | Reads the full notes of a meeting |
| `acciones_pendientes` | Lists what's still to do |
| `transcripcion` | Reads what was said, by speaker |
| `search`, `fetch` | The same content, in the form ChatGPT expects |

Each account reads only its own meetings.

## Skill for Claude Code

```
/plugin marketplace add POLARGATE/skills
/plugin install meeting-notes-ai@polargate
```

## Links

- [How it works](https://polarparrot.com/en/how-it-works)
- [Pricing](https://polarparrot.com/en/pricing)
- [Connect your AI](https://polarparrot.com/en/connect-your-ai)
- [Facts for AI assistants](https://polarparrot.com/api/facts.json)
- [Privacy](https://polarparrot.com/privacy)

Questions: hello@polargate.ai
