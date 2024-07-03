---
sidebar_position: 14
sidebar_label: get_position
hide_title: false
---

import { Highlight } from "../../../../../src/components/Highlight.js";

# get_position


## Input

```typescript
  exchange: string;
  currency: string;
```

## Return

```typescript
  position: Position | None;
```
> Check [Position](/docs/developer/api/python/ca-objects/position)

## Example

To get position size, and to print available and total size. 
Before the limit price order is successfully traded, only available size would decrease. After the limit price order is traded, total size would decrease.

Note `get_position` will return the SAME response each time the callback is triggered. Recalling `CA.get_position` will not get the updated result.  The result will be upated the next time the callback is triggered. We are improving this experience  - you can leverge `on_order_state_change` to trigger side effect

```python
exchange, pair, base, quote = CA.get_exchange_pair()
long_position = CA.get_position(exchange, pair, CA.PositionSide.LONG)
available_long_position_size = 0
if long_position:
    available_long_position_size = long_position.available_size
    total_long_position_size = long_position.total_size
    CA.log('available long position size: ' + str(available_long_position_size))
    CA.log('total long position size: ' + str(total_long_position_size))

short_position = CA.get_position(exchange, pair, CA.PositionSide.SHORT)
available_short_position_size = 0
if short_position:
    available_short_position_size = short_position.available_size
    total_short_position_size = short_position.total_size
    CA.log('available short position size: ' + str(available_short_position_size))
    CA.log('total short position size: ' + str(total_short_position_size))
```

