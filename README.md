<div align="center">

<img src="snap/gui/lightpanda.png" alt="Lightpanda logo" width="128" />

# Lightpanda

**A headless browser for AI agents and web automation**

[![lightpanda](https://snapcraft.io/lightpanda/badge.svg)](https://snapcraft.io/lightpanda)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [Lightpanda](https://github.com/lightpanda-io/browser), a browser with JavaScript support, CDP, MCP and a built-in AI agent.

</div>

---

## Getting Started

<a href="https://snapcraft.io/lightpanda"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install lightpanda
lightpanda fetch --dump markdown https://example.com
```

Run `lightpanda serve` to let Puppeteer or Playwright connect to `ws://127.0.0.1:9222`. Nothing starts automatically.

## Configure

There are no `snap set` options. Use `lightpanda --help` and the [upstream documentation](https://lightpanda.io/docs) for application settings. Provider API keys are passed through environment variables; telemetry is disabled by default.

To connect an MCP client, add:

```json
{
  "mcpServers": {
    "lightpanda": {
      "command": "/snap/bin/lightpanda",
      "args": ["mcp"]
    }
  }
}
```

Authentication data is stored in `~/snap/lightpanda/common/.local/share/lightpanda`. Agent preferences and history are saved in the current directory; run the agent inside your project folder.

```bash
sudo snap connect lightpanda:removable-media   # optional: /media, /mnt
```

## Limitations

- Lightpanda has no desktop window or full visual rendering. PNG/PDF output is text-only, and some browser APIs are not implemented.
- Scripts and downloads must use a non-hidden home folder or connected removable storage. Hidden host configuration is not shared with the snap.
- Google Vertex authentication through a host-installed `gcloud` is unavailable. Use Vertex express mode with an API key or another supported provider.

## Build

```bash
git clone https://github.com/sidalit/lightpanda-snap.git
cd lightpanda-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/lightpanda-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/lightpanda-io/browser/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/lightpanda-snap/blob/main/LICENSE).
