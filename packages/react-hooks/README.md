# @solana/react-hooks

React bindings for the `@solana/client-core` Solana client.

This package exposes a `<SolanaClientProvider>` that wraps the headless client along with ergonomic hooks for common workflows (cluster status, wallet connection, SOL transfers, SPL tokens, balances, etc.).

> **Status:** Experimental – APIs may change frequently while the POC evolves.

## Quick start

```tsx
import { SolanaClientProvider, useBalance, useConnectWallet, useWallet } from '@solana/react-hooks';

function WalletButton() {
    const connectWallet = useConnectWallet();
    return <button onClick={() => connectWallet('phantom')}>Connect Phantom</button>;
}

function WalletStatus() {
    const wallet = useWallet();
    const balance = useBalance(wallet.status === 'connected' ? wallet.session.account.address : undefined);
    if (wallet.status !== 'connected') {
        return <span>Wallet is {wallet.status}</span>;
    }
    return <span>Lamports: {balance.lamports?.toString() ?? '…'}</span>;
}

export function App({ children }) {
    return (
        <SolanaClientProvider
            config={{
                commitment: 'confirmed',
                endpoint: 'https://api.devnet.solana.com',
                websocketEndpoint: 'wss://api.devnet.solana.com',
            }}
        >
            <WalletButton />
            <WalletStatus />
            {children}
        </SolanaClientProvider>
    );
}
```

## Scripts

- `pnpm build` – run both JS compilation and type definition emit
- `pnpm test:typecheck` – strict type-checking without emit
- `pnpm lint` / `pnpm format` – Biome-powered linting and formatting
