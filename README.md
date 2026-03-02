# xToken Flash Loan NAV Manipulation Exploit — PoC

> **Educational Purpose Only** — This PoC is created for security research and education
> purposes only. It runs against a fork, not mainnet.

## Quick Start

```bash
git clone https://github.com/NomosLabs-Security/poc-xtoken-2021
cd poc-xtoken-2021
forge install foundry-rs/forge-std --no-git
forge test -vvvv
```

## Details

- **Exploit Date:** 2021-05-12
- **Fork Block:** #12419918
- **Expected Output:** Flash loan NAV manipulation via Balancer pool distortion, mint at deflated price
- **Full Analysis:** [NomosLabs Security Intelligence Archive](https://nomoslabs.io/archive/xtoken-2021)

## Description

xToken's xSNXa wrapper token calculated NAV from Balancer pool reserves.
Flash loans could distort these reserves, allowing minting at deflated NAV
and redeeming at real NAV. The attacker:

1. Flash-loaned large amounts of ETH and SNX
2. Dumped SNX on Balancer pool to crash SNX price and xSNXa NAV
3. Minted xSNXa at deflated NAV (receiving excess tokens)
4. Restored Balancer pool by buying back SNX
5. Redeemed xSNXa at restored NAV, extracting ~$24M profit

## RPC Providers

```
Alchemy:   https://eth-mainnet.alchemyapi.io/v2/YOUR_KEY
Infura:    https://mainnet.infura.io/v3/YOUR_KEY
QuickNode: https://YOUR_ENDPOINT.quiknode.pro/YOUR_KEY
```

## License

MIT — For educational use only.
