# M14U

This is the main M14U repository. We're porting the backend from Cloudflare Workers to Oracle. The port is in progress, and the setup below still uses the Workers backend. The [legacy Workers build](https://github.com/devsanthoshmk/m14u-workers-v4) remains in its original repository.

M14U is a music player for the web and Android. Both use the same React UI. On Android, Capacitor packages that UI and connects it to a native Kotlin player built on Media3. The Cloudflare Worker provides catalog metadata; audio is resolved and played by the client.

## Run locally

```bash
pnpm install --frozen-lockfile
pnpm dev
```

Vite serves the UI and mounts a local metadata API under `/api`. Search and playback still need network access to their upstream providers.

## Build and test

```bash
pnpm build          # Static web build in dist/
pnpm typecheck
pnpm test:ui
pnpm lint
pnpm android:build  # Requires the Android SDK and JDK
```

## Documentation

- [Setup and environment](docs/SETUP.md) — local development, hosting, and build configuration.
- [Architecture](docs/ARCHITECTURE.md) — UI and state ownership, catalog requests, and playback on both platforms.
- [Android](docs/CAPACITOR.md) — native plugins, APK builds, updates, and device checks.
- [Live resolver setup](docs/LIVE-RESOLVER-SETUP.md) — optional signed updates to Android stream resolution.
- [Console API](docs/CONSOLE-API.md) — browser testing through `window.m14u`.
- [Agent guide](AGENTS.md) — code entry points and change checks.
