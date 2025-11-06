# @solana/client-core

> Framework-agnostic Solana client orchestration layer that wraps `@solana/kit` primitives with a higher-level API inspired by modern web3 client tooling.

This package is not meant for production yet. It showcases the building blocks for a future `@solana/client` release:

- A headless client factory that bootstraps RPC transports, subscriptions, and a composable state store.
- Framework agnostic actions and watchers that make building Solana experiences less verbose.
- Optional Zustand integration so apps can opt-in to a ready-made store or supply their own.
- Wallet Standard helpers (`createWalletStandardConnector`, `watchWalletStandardConnectors`) so you can surface browser wallets without adopting a framework-specific adapter.

## Scripts

- `pnpm build` - runs both `compile:js` and `compile:typedefs`
- `pnpm test:typecheck` - validates TypeScript types without emitting
- `pnpm lint` / `pnpm format` - Biome-powered linting and formatting

## Status

This POC prioritizes API ergonomics and testable primitives. Expect rapid iteration and breaking changes.
