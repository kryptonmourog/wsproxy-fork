# wsproxy-fork

**English** | [Русский](README.ru.md)

A fork of [mautrix-wsproxy](https://github.com/mautrix/wsproxy), which passes the homeserver's appservice
transactions to a bridge over a websocket, so the bridge can run on another server without opening ports.

## Why it exists

[telegram-bridge-advanced](https://github.com/kryptonmourog/telegram-bridge-advanced) often runs on a separate server: in some countries
Telegram isn't reachable from the Matrix server. Upstream wsproxy drops the to-device events and the
one-time/fallback key counts of transactions (MSC2409, MSC3202), and end-to-bridge encryption doesn't work without
them. This fork forwards them. Without encryption it works the same as upstream.

## Usage

- With matrix-docker-ansible-deploy: [telegram-bridge-advanced-ansible](https://github.com/kryptonmourog/telegram-bridge-advanced-ansible)
  installs it on the Matrix server by default.
- Manually: image `ghcr.io/kryptonmourog/wsproxy-fork:<version>`, set up like upstream (`example-config.yaml`,
  [upstream README](https://github.com/mautrix/wsproxy#readme)); the homeserver needs MSC2409 and MSC3202
  enabled for encryption.

## The project

| Repository | What it is |
|---|---|
| [telegram-bridge-advanced](https://github.com/kryptonmourog/telegram-bridge-advanced) | the bridge itself: code, images, installation guide, releases |
| [mautrix-go-fork](https://github.com/kryptonmourog/mautrix-go-fork) | the fork of mautrix-go the bridge is built with |
| **wsproxy-fork** (you are here) | the websocket proxy for a bridge on a separate server, with encryption |
| [telegram-bridge-advanced-ansible](https://github.com/kryptonmourog/telegram-bridge-advanced-ansible) | installation with matrix-docker-ansible-deploy, including on a separate server |

## License

AGPL-3.0, like mautrix-wsproxy.
