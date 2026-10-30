# scripts-solana

![Solana](https://img.shields.io/badge/Solana-Devnet-9945FF?logo=solana&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript&logoColor=white)
![Metaplex](https://img.shields.io/badge/Metaplex-Core%20%2B%20Token%20Metadata-00D18C?logo=metaplex&logoColor=white)
![Irys](https://img.shields.io/badge/Storage-Irys-FF6A00)
![Status](https://img.shields.io/badge/status-live%20on%20devnet-success)

Scripts for creating SPL tokens and NFTs on Solana devnet.

---

## Setup

### 1. Add your wallet

Place your devnet wallet keypair file at the project root:

```
root/
└── devnet-wallet.json   ← here
```

It should be a JSON array of numbers, e.g. `[174, 23, ...]`.

### 2. Install dependencies

```bash
npm install
```

```bash
npm install --save-dev @types/node ts-node typescript
```

### 3. Add your image

Place your image at the project root.

```
root/
└── image.jpeg   ← here
```

---

> Before running the scripts, go through these docs:
> - [Solana token docs](https://solana.com/docs/tokens) — mint accounts, token accounts, and ATAs
> - [Solana Kit](https://www.solanakit.com/) — the JS SDK used for building and sending transactions
> - [Metaplex Token Metadata](https://www.metaplex.com/docs/smart-contracts/token-metadata) — attaching metadata to SPL tokens
> - [Metaplex Core](https://www.metaplex.com/docs/smart-contracts/core) — the NFT standard used in the NFT scripts

## SPL Token

Uses **@solana/kit** and **@solana-program/token** for transactions, and **mpl-token-metadata** via UMI for on-chain metadata.

| Script | Command | What it does |
|---|---|---|
| `spl_init.ts` | `npm run spl:init` | Creates a new mint account |
| `spl_metadata.ts` | `npm run spl:metadata` | Attaches a name, symbol, and URI to the mint |
| `spl_mint.ts` | `npm run spl:mint` | Creates your associated token account and mints tokens into it |
| `spl_transfer.ts` | `npm run spl:transfer` | Sends tokens to another wallet i.e ata to ata |

Run them in order. Each script logs the addresses/signatures you'll need to paste into the next one.

---

## NFT

Uses **@solana/kit** and **mpl-core** via UMI. Images and metadata are stored on Irys (decentralized storage).

| Script | Command | What it does |
|---|---|---|
| `nft_image.ts` | `npm run nft:image` | Uploads your image to Irys, logs the image URI |
| `nft_metadata.ts` | `npm run nft:metadata` | Builds the metadata JSON and uploads it, logs the metadata URI |
| `nft_mint.ts` | `npm run nft:mint` | Mints the NFT on-chain using the metadata URI |

Run them in order. Paste the URI logged by each step into the next script before running it.

---

## ✅ Live Devnet Run

All 7 scripts executed successfully end-to-end on Solana devnet.

### SPL Token

| | |
|---|---|
| **Mint** | [`6Gs9xV2xb5K3y5hndqJ1fjDHCiE3nyLxGU7vwfFoJzAN`](https://explorer.solana.com/address/6Gs9xV2xb5K3y5hndqJ1fjDHCiE3nyLxGU7vwfFoJzAN?cluster=devnet) |
| **Metadata** | attached (name, symbol, URI) |
| **Minted to ATA** | [`AYzG1HrGnBRwr7F6wrhpCQErX9bDTyTbpNuBk9XV7dKs`](https://explorer.solana.com/address/AYzG1HrGnBRwr7F6wrhpCQErX9bDTyTbpNuBk9XV7dKs?cluster=devnet) |
| **Transferred to** | [`BDvegpXrgyThCtAV33wHAxjFFXmkfcqZqmjPJEcQtXg8`](https://explorer.solana.com/address/BDvegpXrgyThCtAV33wHAxjFFXmkfcqZqmjPJEcQtXg8?cluster=devnet) |

### NFT (Metaplex Core)

| | |
|---|---|
| **Image** | [Irys gateway](https://gateway.irys.xyz/9XJCCb5Q1oK7raP3xDrU5LhGDPp1HDC2ohZE4oBhk6uH) |
| **Metadata JSON** | [Irys gateway](https://gateway.irys.xyz/EAGWX2m8kN2AMxpfN4b1ox6EFBw6VLpBtsYSzL9W2TwZ) |
| **Asset** | [`FnjFpSgtwy1K4PQ1sAih96BGEZE6rQ4SzH3pXoq2MQcE`](https://explorer.solana.com/address/FnjFpSgtwy1K4PQ1sAih96BGEZE6rQ4SzH3pXoq2MQcE?cluster=devnet) |
| **Mint tx** | [`2zVizubd3NSLQ42FikTvYFzW4jePc5Cz4hHr1MMxPKkaH9c5sFzgsRZdTLpmg57Fr7hbm6QMbUYRJUk7Fx5BfZCs`](https://explorer.solana.com/tx/2zVizubd3NSLQ42FikTvYFzW4jePc5Cz4hHr1MMxPKkaH9c5sFzgsRZdTLpmg57Fr7hbm6QMbUYRJUk7Fx5BfZCs?cluster=devnet) |
