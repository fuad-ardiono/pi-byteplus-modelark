# pi-byteplus-modelark

[![npm version](https://img.shields.io/npm/v/pi-byteplus-modelark.svg?style=flat-square)](https://www.npmjs.com/package/pi-byteplus-modelark)
[![pi.dev package](https://img.shields.io/badge/pi.dev-package-blue?style=flat-square)](https://pi.dev/packages/pi-byteplus-modelark)
[![MIT License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)

Pi coding agent extension that registers BytePlus ModelArk as a custom OpenAI-compatible provider, unlocking access to all supported coding models directly within the pi TUI.

**One API key covers all models.** No need to configure per-model keys.

## Key Features
- **Seamless ModelArk Integration**: Adds BytePlus ModelArk as a first-class provider in pi's model registry
- **OpenAI Compatibility**: Works with pi's existing OpenAI-style tooling and prompts
- **Multi-Model Support**: Access all BytePlus ModelArk coding models (DeepSeek, GLM, Kimi, Seed, and more)
- **Single API Key**: One Coding Plan API key works across all models — no per-model configuration needed

## Installation

```bash
pi install npm:pi-byteplus-modelark
```

## Setup

You need a BytePlus ModelArk API key. Create one at [https://console.byteplus.com](https://console.byteplus.com).

Set the `BYTEPLUS_API_KEY` environment variable:

```bash
export BYTEPLUS_API_KEY="ark-your-api-key-here"
```

Add it to your `~/.bashrc` or `~/.zshrc` to persist across sessions.

## Usage

### Start pi and pick a model interactively (Recommended)

```bash
pi
```

Then use `/model` to select a BytePlus model from the list.

**Note:** Some BytePlus model IDs (like `glm-5.1`, `kimi-k2.5`) also exist in other built-in providers (opencode, zai). To avoid confusion, we recommend using `/model` to select models interactively.

### Specify a model directly

```bash
# Auto-routed model (recommended)
pi --model ark-code-latest

# Use full provider/model syntax for models with ID collisions
pi --model byteplus/glm-5.1
pi --model byteplus/kimi-k2.5

# Models without collisions work directly
pi --model dola-seed-2.0-pro
pi --model deepseek-v3.2
```

## Available Models

| Model ID | Name | Context | Max Output |
|----------|------|---------|------------|
| `ark-code-latest` | ModelArk Auto (recommended) | 128K | 8.2K |
| `dola-seed-2.0-pro` | Seed 2.0 Pro | 262K | 128K |
| `dola-seed-2.0-lite` | Seed 2.0 Lite | 262K | 128K |
| `dola-seed-2.0-code` | Seed 2.0 Code | 262K | 128K |
| `bytedance-seed-code` | ByteDance Seed Code | 128K | 8.2K |
| `glm-5.1` | GLM 5.1 | 204K | 65.5K |
| `glm-4.7` | GLM 4.7 | 204K | 65.5K |
| `kimi-k2.5` | Kimi K2.5 | 262K | 65.5K |
| `gpt-oss-120b` | GPT-OSS 120B | 128K | 8.2K |
| `deepseek-v3.2` | DeepSeek V3.2 | 131K | 8.2K |

List all available models at any time:

```bash
pi --list-models
```

## Important Notes

- **Use the Coding Plan endpoint**: This extension uses `https://ark.ap-southeast.bytepluses.com/api/coding/v3` (Coding Plan URL). Do **NOT** switch to the base model URL (`/api/v3`) — that will incur additional charges outside your Coding Plan quota.
- **API Key**: Create your API key at [BytePlus Console](https://console.byteplus.com).

## Contributing
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit changes with SemVer-compliant messages
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a pull request

## Support
- Open an issue: [GitHub Issues](https://github.com/irahardianto/pi-byteplus-modelark/issues)

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


---

<p align="center">
  Built with ❤️ for the Developer Community
</p>