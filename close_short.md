---
sidebar_position: 8
sidebar_label: close_short (FUTURES)
hide_title: false
---

import { Highlight } from "../../../../../src/components/Highlight.js";

# close_short (FUTURES)

<Highlight color="#ffba00"> This function can only be used in trade(). </Highlight>

To put one close_short order. Each period can put at max 500# orders.

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

To put one close_short order with market price for 1 amount. It is not necassery to set price with market price order.

```python
exchange, pair, base, quote = CA.get_exchange_pair()
short_position = CA.get_position(exchange, pair, CA.PositionSide.SHORT)
if short_position and short_position.available_size >= 1:
    CA.close_short(exchange, pair, 1, CA.OrderType.MARKET)
```

To put one close_short order with limit price for 1 amount. The limit price is set as close_price.

```python
exchange, pair, base, quote = CA.get_exchange_pair()
close_price = candles[exchange][pair][0]['close']
short_position = CA.get_position(exchange, pair, CA.PositionSide.SHORT)
if short_position and short_position.available_size >= 1:
    CA.close_short(exchange, pair, 1, CA.OrderType.LIMIT, close_price)
```
