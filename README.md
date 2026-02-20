# Bitcoin PSBT Signing Tool (`signer.html`)

Single-file web app for signing and broadcasting Bitcoin PSBTs with **UniSat** (extension or mobile). Works with **TLB_Pocket_Minter** Telegram bot for BRC-20 minting and airdrops.

---

## Quick start

1. Open `signer.html` in a browser (or serve the folder).
2. Connect **UniSat** (extension or “Open in UniSat App” / deeplink on mobile).
3. **Sign** tab: paste or upload PSBT (hex/base64 or `.json`/`.psbt` from the bot), review, sign.
4. **Broadcast** tab: paste signed PSBT or raw tx hex, choose **Fractal Bitcoin (FB)** or **Bitcoin (BTC)**, then broadcast via UniSat or Mempool API.

---

## Tabs

| Tab | Purpose |
|-----|--------|
| **Sign** | Paste/upload PSBT → decode & show details → sign with UniSat (or paste signed PSBT from app). Optional address field; wallet address used if empty. |
| **Broadcast** | Paste signed PSBT or raw tx hex. Choose chain (FB or BTC), then **Broadcast via UniSat** or **Broadcast via Mempool**. |
| **Inspect PSBT** | Decode any PSBT **client-side**: inputs/outputs, scripts, opcodes, sighash, BIP32 paths, Taproot keys, **change vs payment** (by key match), **addresses** (base58/bech32/bech32m). “Use current PSBT from Sign tab” copies Sign tab data and runs decode. |
| **Sign Message** | **BIP-322** message signing. Output is base64 BIP-322 simple signature (e.g. `AkgwRQIhAI/...`). Requires connected UniSat (`signMessage(..., 'bip322-simple')`). |

---

## Wallet block

When connected: **address**, **pubkey** (short, click to copy), **balance** (UniSat `getBalance()`). Refresh button to update balance.

---

## Requirements & environment

- **UniSat** wallet (browser extension or mobile app).
- **No server required**: decode/inspect and key handling are client-side; optional external API used for a richer decode in Sign tab when available.
- **Broadcast**: uses Mempool API (FB: `mempool.fractalbitcoin.io`, BTC: `mempool.space`) or UniSat’s broadcast.
- **Languages**: EN / RU / ZH in the “How to Use” section.

---

## Airdrop note

For airdrops: sign with the **source address** (the one that holds the BRC-20 inscriptions), not the minting address.

---

## File

- **`signer.html`** — All HTML, CSS, and JS in one file. Drop-in; no build step. Ensure `images/TLB-Icon-TransBG.png` exists if you want the favicon.
