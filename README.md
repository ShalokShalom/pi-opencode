# opencode-pi

Extension for the [pi](https://github.com/mariozechner/pi-coding-agent) coding agent, to add OpenCode as a provider. 🙂

## Features

- **40+ models**: GPT, Claude, Gemini, GLM, Kimi, Qwen, MiniMax, and more:
  (**Complete List**)[https://models.dev/?sort=provider&order=asc&search=OpenCode] (raise an issue, if you find a model in this list, thats not available with this extension)
- **opencode-go**: Subscription service (https://opencode.ai/zen/go)
- **opencode-zen**: Pay-as-you-go (https://opencode.ai/zen)

## Prerequisites

- Install [pi](https://github.com/earendil-works/pi) and a npm implementation (npm, yarn, pnpm)
- Create an OpenCode account: https://opencode.ai/auth 
- Pay for the service (Go is strongly recommended), and [copy the API key.](https://opencode.ai/workspace/wrk_01KR5R14VMRPHGAACY61PYWNM6/keys) 

## Installation

Add this to your pi `settings.json` (`~/.pi/agent/settings.json`):

```json
{
  "packages": [
    "git:https://github.com/ShalokShalom/pi-opencode.git"
  ]
}
```

### Recommended Configuration

This is currently the recommended setup, so long as M3 is free on the Zen tier, and generally the strongest model on the subscription model. 
(The free version is limited to a 256k context window, while the paid Go subscription is able to utilize the full 1 million token.)

```
{
  "packages": [
    "git:https://github.com/ShalokShalom/pi-opencode.git"
  ],
  "model": "opencode-go-anthropic/minimax-m3",
  "small_model": "opencode-zen-anthropic/minimax-m3-free"
}
```

## Configuration

Add this line to your shell configuration: 

Bash, Zsh, etc

```bash
export OPENCODE_API_KEY="your-api-key-here"
```

Fish

```fish
set -Ux OPENCODE_API_KEY "your-api-key-here"
```

(`~/.bashrc`, `~/.zshrc`, `~/.config/fish/config.fish`)

### 3. Open pi

**First**, open a new shell to load the config (`exec bash`, `exec zsh`, `exec fish`).  
**Then** open `pi`.

## Usage

### Select a provider and model

Type `/model` to select a model. 

You can also select one directly via the full path:

```bash
/model opencode-zen/gpt-5.1
/model opencode-go-anthropic/minimax-m3
```

### Note about MiniMax

MiniMax uses the Anthropic Messages API.  

| Provider | API | Endpoint |
|----------|-----|----------|
| opencode-go | OpenAI Chat Completions | https://opencode.ai/zen/go/v1/chat/completions |
| opencode-zen | OpenAI Chat Completions | https://opencode.ai/zen/v1/chat/completions |
| opencode-go-anthropic | Anthropic Messages | https://opencode.ai/zen/go/v1/messages |
| opencode-zen-anthropic | Anthropic Messages | https://opencode.ai/zen/v1/messages |

## Development

```bash
# Clone the repository
git clone https://github.com/ShalokShalom/pi-opencode.git
cd pi-opencode

# Test locally
pi -e ./src/index.ts
```

## Troubleshooting

### "No API key" error

```bash
echo $OPENCODE_API_KEY
```

If empty, set it as shown in [step 2](#2-set-the-environment-variable)

### Extension not loading

Run `/reload` after changes.

### Model not found

Verify that the model name is correct; [they are case-sensitive.](https://models.dev/?sort=provider&order=asc&search=OpenCode)

## License

MIT

## Links

- [pi coding agent](https://github.com/mariozechner/pi-coding-agent)
- [OpenCode Go](https://opencode.ai/docs/go/)
- [OpenCode Zen](https://opencode.ai/docs/zen/)
- [OpenCode](https://opencode.ai/auth)
