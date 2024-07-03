---
sidebar_position: 12
sidebar_label: get_exchange_pair
hide_title: false
---

import { Highlight } from "../../../../../src/components/Highlight.js";

# get_exchange_pair

To get single exchange pair information.

## Return

```typescript
  exchange_pair: ExchangePair
```
> Check [ExchangePair](/docs/developer/api/python/ca-objects/exchange-pair)

## Example

To get exchange pair information.

```py
exchange, pair, base, quote = CA.get_exchange_pair()
```
