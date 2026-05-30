# github-pay — live demo 🤖💸

**Open a pull request here and an AI agent automatically pays you 10 testnet HBAR** — settled on Hedera with an on-chain receipt. No human in the loop.

Powered by [`@jmgomezl/github-pay`](https://github.com/jmgomezl/hak-plugin-github-pay) · server health: [github-pay.aivylabs.xyz/health](https://github-pay.aivylabs.xyz/health)

---

## Try it (≈60 seconds)

1. Get a **Hedera testnet** account (free at [portal.hedera.com](https://portal.hedera.com)) — an id like `0.0.12345`.
2. Edit [`CONTRIBUTORS.md`](CONTRIBUTORS.md) and add a line with your GitHub handle: `- @yourhandle`
3. Open the PR. In the **description**, include your account: `Hedera account: 0.0.YOURID` (the PR template prompts you).
4. A bot registers your account on the public **IDENTITIES** topic, labels the PR `bounty-10`, and **auto-merges** it.
5. On merge, the agent transfers **10 HBAR** to you and seals a **receipt on Hedera**. 🎉

You'll see the transfer and receipt on [Hashscan](https://hashscan.io/testnet) within seconds.

---

## The enterprise controls are real — and you can try to break them

This isn't a faucet. Every payout runs through on-chain financial controls:

- **Per-contributor cap: 10 HBAR** — you can claim **once**. Sybil/multi-account gets you nothing extra.
- **Monthly cap: 500 HBAR** — the pool is mathematically **undrainable** past the ceiling.
- **Idempotent** — re-merges and webhook retries never double-pay.
- **Immutable receipts** — every payment is sealed on Hedera Consensus Service, independently verifiable.
- **Admin/payer key separation** — the spending policy lives on a `submitKey`-locked topic; the key that *pays* cannot *raise its own cap* (proven on-chain).

So the interesting demo isn't "free money" — it's watching the **caps hold under adversarial, self-serve load**.

---

*Self-serve demo mode uses auto-merge. In a real deployment the GitHub PR review + merge is the human approval gate (4-eyes); the cap is the financial control.*
