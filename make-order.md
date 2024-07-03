---
sidebar_position: 2
sidebar_label: Make an Order
hide_title: false
---

# Make an Order

In the previous article, we learned how to get K bar data. In this article, we will trade based on the K bar data

## Calculate SMA(Simple Moving Average)

Use SMA as an example, we use golden cross and death cross of long and short period of MA to determine the buying and selling points.

In `__init__` function, we set long period as 10 and short period as 5.

```py
self.long_window_size = 10
self.short_window_size = 5
```

We could save historical close price into `close_price_history` to calculate SMA.

If the data is not enough, `talib` would get `NaN`; we cannot determine golden cross or death cross at this point. We could directly return and wait for the next K bar.

```py
def trade(self, candles):
    exchange, pair, base, quote = CA.get_exchange_pair()

    # get the latest 10 candles
    if len(candles[exchange][pair]) < self.long_window_size + 1:
        return
    candles[exchange][pair] = candles[exchange][pair][:self.long_window_size + 1]
    # use close price
    close_price_history = [candle['close'] for candle in candles[exchange][pair]]
```

`candles` is sorted from the newest to the oldest; while talib consumes input from the oldest to the newest. Therefore, we reverse the data here.

```py
    # convert to chronological order for talib
    close_price_history.reverse()
```

Convert to `np.array` which talib accepts. Use talib to calculate long and short period SMA.

```py
    # convert np.array
    close_price_history = np.array(close_price_history)
    long_ma_history = talib.SMA(close_price_history, self.long_window_size)
    short_ma_history = talib.SMA(close_price_history, self.short_window_size)
```

## Make an order

Use CA.get_balance to get the available balance.

```py
    # get available balance
    base_balance = CA.get_balance(exchange, base)
    quote_balance = CA.get_balance(exchange, quote)
    available_base_amount = base_balance.available
    available_quote_amount = quote_balance.available
```

Use the last 2 values of `long_ma_history` and `short_ma_history` to determine golden cross and death cross.
Make an order after checking the available asset.

```py
    if short_ma_history[-2] < long_ma_history[-2] and short_ma_history[-1] > long_ma_history[-1]:
        CA.log('Golden Cross')
        amount = 0.1
        if available_quote_amount >= amount * close_price_history[-1]:
            CA.log('Buy ' + base)
            CA.buy(exchange, pair, amount, CA.OrderType.MARKET)
        else:
            CA.log('The asset is not enough.')
    elif short_ma_history[-2] > long_ma_history[-2] and short_ma_history[-1] < long_ma_history[-1]:
        CA.log('Death Cross')
        if available_base_amount > 0:
            CA.log('Sell ' + base)
            CA.sell(exchange, pair, available_base_amount, CA.OrderType.MARKET)
        else:
            CA.log('The asset is not enough.')
```

## Complete strategy code

```py
class Strategy(StrategyBase):
    def __init__(self):
        # strategy attributes
        self.period = 60 * 60
        self.subscribed_books = {}
        self.options = {}

        # define your attributes here
        self.long_window_size = 10
        self.short_window_size = 5

    def on_order_state_change(self,  order):
        pass

    def trade(self, candles):
        exchange, pair, base, quote = CA.get_exchange_pair()

        # get the latest 10 candles
        if len(candles[exchange][pair]) < self.long_window_size + 1:
            return
        candles[exchange][pair] = candles[exchange][pair][:self.long_window_size + 1]
        # use close price
        close_price_history = [candle['close'] for candle in candles[exchange][pair]]

        # convert to chronological order for talib
        close_price_history.reverse()
        # convert np.array
        close_price_history = np.array(close_price_history)
        long_ma_history = talib.SMA(close_price_history, self.long_window_size)
        short_ma_history = talib.SMA(close_price_history, self.short_window_size)

        # get available balance
        base_balance = CA.get_balance(exchange, base)
        quote_balance = CA.get_balance(exchange, quote)
        available_base_amount = base_balance.available
        available_quote_amount = quote_balance.available

        if short_ma_history[-2] < long_ma_history[-2] and short_ma_history[-1] > long_ma_history[-1]:
            CA.log('Golden Cross')
            amount = 0.1
            if available_quote_amount >= amount * close_price_history[-1]:
                CA.log('Buy ' + base)
                CA.buy(exchange, pair, amount, CA.OrderType.MARKET)
            else:
                CA.log('The asset is not enough.')
        elif short_ma_history[-2] > long_ma_history[-2] and short_ma_history[-1] < long_ma_history[-1]:
            CA.log('Death Cross')
            if available_base_amount > 0:
                CA.log('Sell ' + base)
                CA.sell(exchange, pair, available_base_amount, CA.OrderType.MARKET)
            else:
                CA.log('The asset is not enough.')
```
