# Drift Emberlens — Maintainer Notes

Short internal notes for maintainers of the Drift Emberlens project.

---

## Naming Conventions

- **Packages**: kebab-case (`drift-emberlens`)
- **Config files**: dot-separated and lowercase (`base.networks.json`)
- **Variables / exports**: camelCase
- **Constants**: SCREAMING_SNAKE_CASE

Network identifiers must match keys in `config/base.networks.json`
(e.g. `base-mainnet`, `base-sepolia`).

---

## Dependency Mapping

Dependencies should come **only from Base / Coinbase ecosystem repositories**.

Typical mapping:
- Network + chain metadata → Base config (`base.networks.json`)
- Wallet / UX → Base-compatible SDKs
- RPC access → Base public RPC endpoints
- Payments / gated access → protocol-level helpers (if applicable)

Avoid duplicating network constants in code — always read from config.

---

## Validation Checklist

Before merging changes, verify:

- [ ] `chainId` values match official Base documentation
- [ ] RPC URLs are reachable and not hardcoded in source files
- [ ] Explorer URLs point to the correct network
- [ ] No secrets or API keys are committed
- [ ] New dependencies align with Base ecosystem usage
- [ ] Config changes do not break default network selection

---

## Notes

- Mainnet is the default network.
- Sepolia is used for testing and development.
- Any new Base network should be added **only** via `base.networks.json`.

_Last updated: initial scaffold_
