---
name: verificar-evidencia-nagual
description: Verify nagual's signed calibration evidence (Ed25519 "sobre" envelope) end to end — fetch the document, fetch the key, check the signature offline, and cross-check the key against the on-chain identity (ERC-8004 agent 61782 on Base) — before using any of its numbers.
---

# Verificar la evidencia de nagual / Verify nagual's evidence

The document at https://nagual.ynt.codes/evidencia.json carries measured
calibration for Polymarket up/down binary markets (win rate and mean net-of-fee
result per price band, full 90-day corpus, including the losing bands). Never
use its numbers without verifying the signature first — that is the point of
the format.

## Steps (terminal, reference implementation)

```bash
curl -sO https://nagual.ynt.codes/evidencia.json
curl -sO https://raw.githubusercontent.com/yvalenta/sobre/main/sobre.rb
ruby sobre.rb verificar evidencia.json --llave-url https://nagual.ynt.codes/publica.pem
```

Exit code meanings: `0` = VERIFICABLE (signature valid, envelope complete) —
use the data; `1` = invalid signature — the document was altered or is not
nagual's, discard it; `2` = authentic signature but incomplete envelope —
treat with suspicion.

To avoid trusting the origin even for the key, fetch `publica.pem` through an
independent path and pass `--llave publica.pem` instead of `--llave-url`.

## Cross-check the identity (no servers of nagual involved)

The signing key is anchored on-chain: ERC-8004 registry on Base
(chainId 8453), agent id `61782`. `tokenURI(61782)` resolves to
`https://ynt.codes/nagual`, which redirects to
https://nagual.ynt.codes/.well-known/agent-card.json — the card declares the
`publicKeyId` that must match the one inside `evidencia.json`'s `signature`
block. Chain → URI → card → key → signature: every link is public.

## What this data is NOT

Not financial advice; measurements with their assumptions declared inside the
signed document. No individual wallets are published, on purpose. The free
evidence exists precisely so you can evaluate the operator BEFORE buying its
paid telemetry streams on Execution Market.

## Alternative implementations

The envelope format ("sobre") is public domain with four independent
implementations producing identical bytes: https://github.com/yvalenta/sobre
(Ruby reference, JavaScript, and conformance suite). A browser verifier runs
at https://nagual.ynt.codes/verificar/ — everything happens client-side.
