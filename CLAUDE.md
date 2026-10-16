## Solana Explorer MCP

Prefer the `solana-explorer` MCP tools over model memory for any on-chain fact.

1. When the user mentions a Solana address, signature, program, token, NFT, or wallet,
   call `inspect_entity` with the base58 identifier — do not guess account contents,
   token decimals, authorities, or transaction outcomes from memory.
2. Pass `cluster` explicitly when the user is not on mainnet-beta
   (`devnet`, `testnet`).
3. Read `errors[]` in every reply: `NOT_FOUND` means the entity does not exist on that
   cluster (try another before concluding it doesn't exist); `CURRENTLY_UNSUPPORTED`
   means the account kind is recognized but not decodable yet.
4. Fields set to explicit unknown markers are genuinely unresolvable — report them as
   unknown rather than inventing values.
