---
sidebar_position: 3
sidebar_label: buy (SPOT)
hide_title: false
title: Buy (SPOT)
description: Python function to buy SPOT
tags:
  - python
---

# buy (SPOT)

To put one buy order. Each period can put at max 500# orders.

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

To put one buy order with market price for 1 amount. It is not necassery to set price with market price order.

```python
exchange, pair, base, quote = CA.get_exchange_pair()
CA.buy(exchange, pair, 1, CA.OrderType.MARKET)
```

To put one buy order with limit price for 1 amount. The limit price is set as close_price.

```python
exchange, pair, base, quote = CA.get_exchange_pair()
close_price = candles[exchange][pair][0]['close']
CA.buy(exchange, pair, 1, CA.OrderType.LIMIT, close_price)
```
