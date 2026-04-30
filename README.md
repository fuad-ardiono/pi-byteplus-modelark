# pi-byteplus-modelark

[![npm version](https://img.shields.io/npm/v/pi-byteplus-modelark.svg?style=flat-square)](https://www.npmjs.com/package/pi-byteplus-modelark)
[![pi.dev package](https://img.shields.io/badge/pi.dev-package-blue?style=flat-square)](https://pi.dev/packages/pi-byteplus-modelark)
[![MIT License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)

Pi coding agent extension that registers ByteDance's BytePlus ModelArk as a custom OpenAI-compatible provider, unlocking access to all supported coding models (DeepSeek, GLM, Kimi, Seed, etc.) directly within the pi TUI.

## Key Features
- **Seamless ModelArk Integration**: Adds BytePlus ModelArk as a first-class provider in pi's model registry
- **OpenAI Compatibility**: Works with pi's existing OpenAI-style tooling and prompts
- **Multi-Model Support**: Access all BytePlus ModelArk coding models (DeepSeek, GLM, Kimi, Seed, and more)
- **Coding Plan Quota**: Uses the Coding Plan endpoint by default — no extra charges

## Installation

### Via pi (Recommended)
```bash
pi install npm:pi-byteplus-modelark
```

### Via npm (Manual)
```bash
# Install globally
npm install -g pi-byteplus-modelark

# Link to pi's extension directory
ln -s $(npm root -g)/pi-byteplus-modelark/extensions ~/.agents/extensions/pi-byteplus-modelark
```

## Configuration

Set your BytePlus ModelArk API key using **one** of these methods:

### Method 1: Environment Variable (Recommended)

Add to your `~/.bashrc`, `~/.zshrc`, or equivalent:

```bash
export BYTEPLUS_API_KEY=your_api_key_here
```

Then restart your shell or run `source ~/.bashrc`.

### Method 2: `--api-key` Flag

Pass the API key directly when starting pi:

```bash
pi --api-key YOUR_API_KEY --model byteplus:ark-code-latest
```

### Method 3: Inline in Extension

Edit `extensions/index.ts` and replace the env var name with your literal key:

```typescript
apiKey: "your_actual_api_key_here",  // NOT recommended for shared/public machines
```

## Usage

### Select a model

Start pi and switch to a BytePlus model via `/model` or `Ctrl+P`, or use the `--model` flag:

```bash
# Auto-routed model (recommended)
pi --model byteplus:ark-code-latest

# Specific model
pi --model byteplus:dola-seed-2.0-pro
pi --model byteplus:kimi-k2.5
```

### Available Models

| Model ID | Display Name | Context | Max Output |
|----------|-------------|---------|------------|
| `ark-code-latest` | ModelArk Auto | 128K | 8K |
| `dola-seed-2.0-pro` | Seed 2.0 Pro | 262K | 128K |
| `dola-seed-2.0-lite` | Seed 2.0 Lite | 262K | 128K |
| `dola-seed-2.0-code` | Seed 2.0 Code | 262K | 128K |
| `bytedance-seed-code` | ByteDance Seed Code | 128K | 8K |
| `glm-5.1` | GLM 5.1 | 205K | 66K |
| `glm-4.7` | GLM 4.7 | 205K | 66K |
| `kimi-k2.5` | Kimi K2.5 | 262K | 66K |
| `gpt-oss-120b` | GPT-OSS 120B | 128K | 8K |
| `deepseek-v3.2` | DeepSeek V3.2 | 131K | 8K |

### Set as Default Provider

Edit `~/.pi/agent/settings.json`:

```json
{
  "defaultProvider": "byteplus"
}
```

### List all available models

```bash
pi --list-models byteplus
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