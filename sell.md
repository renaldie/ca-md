---
sidebar_position: 4
sidebar_label: sell (SPOT)
hide_title: false
---

import { Highlight } from "../../../../../src/components/Highlight.js";

# sell (SPOT)

<Highlight color="#ffba00"> his function can only be used in trade(). </Highlight>

To put one sell order. Each period can put at max 500# orders.

## Input

```typescript
exchange: string;
pair: string;
amount: number;
type: OrderType;
price: number;
```

> Check [OrderType](/docs/developer/api/python/ca-objects/order-type)

## Example

To put one sell order with market price for 0.999 amount. It is not necassery to set price with market price order.

```python
exchange, pair, base, quote = CA.get_exchange_pair()
CA.sell(exchange, pair, 0.999, CA.OrderType.MARKET)
```

To put one sell order with limit price for 0.999 amount. The limit price is set as close_price.

```python
exchange, pair, base, quote = CA.get_exchange_pair()
close_price = candles[exchange][pair][0]['close']
CA.sell(exchange, pair, 0.999, CA.OrderType.LIMIT, close_price)
