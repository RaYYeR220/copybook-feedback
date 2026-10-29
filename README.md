# dreamDEX perps feedback: Somnia Hideki

Six reproducible reports on the dreamDEX perps stack (SDK, RPC, indexer, docs) on Somnia Hideki testnet
(chain 50383), found while building Copybook, an on-chain copy-trading app for dreamDEX perps.

Every report is in [`feedback/`](feedback/), one file per issue, in the bounty's template: title, severity,
area, steps to reproduce, expected, actual, evidence, environment. Each one was reproduced on 2026-10-29
against the public endpoints, and each names the documentation page it was checked against.

| # | Report | Severity | Area |
|---|---|---|---|
| 01 | [Perp voucher: `getPerpVoucherEligibility` returns `eligible: true`, but `VoucherDistributor.claim()` reverts `0x3e31dcc2` for every account](feedback/01-voucher-self-claim-disabled.md) | major | SDK |
| 02 | [Hideki RPC: state reads addressed by block hash fail, so Foundry cannot fork the chain](feedback/02-rpc-block-hash-state-reads.md) | major | API |
| 03 | [Hideki RPC: `eth_getStorageAt` returns `"0x"` for a slot that holds zero](feedback/03-rpc-empty-storage-slot.md) | normal | API |
| 04 | [SDK: a write from a signer with no STT throws `ContractRevertError` instead of `RpcError`](feedback/04-sdk-unfunded-signer-reported-as-revert.md) | normal | SDK |
| 05 | [Indexer: `MarginEvent` ordered by `blockNumber` fails with "database query error" after ~11 s](feedback/05-indexer-order-by-blocknumber-times-out.md) | normal | API |
| 06 | [Docs: Hideki block time, explorer and Multicall3 are out of date](feedback/06-docs-hideki-network-facts-stale.md) | normal | docs |

## Reproduce

[`feedback/repro/`](feedback/repro/) has one small script per report. They use public endpoints only, need
no key and send no transaction.

```sh
cd feedback/repro
npm ci
node 01-voucher-self-claim.ts    # Node 22.18+ runs TypeScript directly
```

See [`feedback/README.md`](feedback/README.md) for the endpoint overrides and the Foundry steps of report 02.

## License

MIT
