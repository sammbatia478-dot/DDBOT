# DDBOT

## Overview
DDBOT is a Go-based QQ group bot framework that supports push notifications for:
- Bilibili live streams and dynamic posts
- Douyu live streams
- YouTube live streams and videos
- Huya live streams
- ACFUN live streams
- Weibo posts
- TwitCasting streams

## Architecture
- **Language**: Go 1.24
- **Entry point**: `cmd/main.go`
- **Bot logic**: `bot.go` (Run/SetUpLog)
- **Core modules**: `lsp/` directory (bilibili, douyu, huya, youtube, weibo, acfun, twitcasting)
- **Database**: BuntDB (local embedded key-value store) — `.lsp.db`
- **Config**: `application.yaml` (auto-generated on first run)

## Build & Run
```bash
# Build
go build -o DDBOT ./cmd/

# Run
./DDBOT
```

## Configuration
The bot reads from `application.yaml` in the working directory. Key settings:
- `bot.account` / `bot.password` — QQ account credentials (optional, QR code login available)
- `bilibili.SESSDATA` / `bilibili.bili_jct` — Bilibili account cookies
- `sign-server` — Optional sign server URL
- `logLevel` — Logging level (default: info)

## Workflow
- **Start application**: Runs `./DDBOT` as a console process
- No web frontend — this is a CLI/bot application

## Deployment
- Target: VM (always-running bot)
- Build: `go build -o DDBOT ./cmd/`
- Run: `./DDBOT`

## First-Time Setup
1. Run the bot — it will generate `application.yaml`
2. Edit `application.yaml` with your QQ credentials
3. On first run, use QR code to login
4. Send `/whosyourdaddy` in private chat to the bot to get admin rights
5. Send `/help` to see available commands
