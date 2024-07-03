---
sidebar_position: 3
sidebar_label: pandas
hide_title: false
---

import { Highlight } from "../../../../../src/components/Highlight.js";

# pandas

Use `pd` to access [pandas] function. (https://pandas.pydata.org)

### Example

Use pandas series data frame.

```python
exchange, pair, base, quote = CA.get_exchange_pair()
candle = candles[exchange][pair][0]
data = {
    'name': ['open', 'high', 'low', 'close'],
    pair: [candle['open'], candle['high'], candle['low'], candle['close']],
}
df = pd.DataFrame(data)
Log(str(df.at[1, pair]))

