# NIP-67 (EOSE Completeness) on LiberNet

> EOSE Completeness Hint, as used by the **LiberNet** apps.

**Official spec:** [nostr-protocol/nips · 67.md](https://github.com/nostr-protocol/nips/blob/master/67.md)
**Status upstream:** `draft` `optional`
**Maintainer of this repo:** Luciano "Barak" Casalunga ([@lucianocasalunga](https://github.com/lucianocasalunga)) · [libernet.app](https://libernet.app)

## My role

I took part in the creation of NIP-67, and it runs across the LiberNet apps.

## Why NIP-67 matters for LiberNet

LiberNet apps load long feeds and histories. NIP-67 lets the relay say in the `EOSE` message whether everything was sent, so the apps stop guessing and stop making extra requests.

## How it works (quick reference)

| Hint | Meaning |
|------|---------|
| `"finish"` | Every stored matching event was sent; don't paginate |
| `"more"` | There are more stored events; paginate |
| `"auth"` | More events may be available after NIP-42 `AUTH` |

Old clients simply ignore the third element, so it is fully backwards compatible.

### Example

```
["REQ", "feed", {"authors": ["<hex pubkey>"], "kinds": [1]}]
["EVENT", "feed", {...}]
["EOSE", "feed", ["more"]]
```

## Related LiberNet NIPs

[NIP-43](https://github.com/lucianocasalunga/nip-43) · [NIP-45](https://github.com/lucianocasalunga/nip-45) · [NIP-50](https://github.com/lucianocasalunga/nip-50) · [NIP-66](https://github.com/lucianocasalunga/nip-66) · [NIP-70](https://github.com/lucianocasalunga/nip-70) · [NIP-77](https://github.com/lucianocasalunga/nip-77) · [NIP-86](https://github.com/lucianocasalunga/nip-86) · [NIP-95 (my proposal)](https://github.com/lucianocasalunga/nip-95)

---
Nostr since 2021 · Part of the LiberNet ecosystem
