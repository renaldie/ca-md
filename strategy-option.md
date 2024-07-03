---
sidebar_position: 3
sidebar_label: Strategy Parameters
hide_title: false
---

import { Highlight } from "../../../../src/components/Highlight.js";

# Strategy Parameters

### Reserved parameters

Reserved parameters cannot be used for other purposes.

| Variable      | Description                                                     | Type    | Default Value |
| ------------- | --------------------------------------------------------------- | ------- | ------------- |
| exchange_fee  | set exchange fee for backtests and simulations. (default: 0.1%) | Number  | 0.001         |
| spread        | set spread for backtests and simulations.                       | Number  | 0             |
| leverage      | set leverage for live trades.                                   | Number  | 1             |
| IS_DEBUG      | set True to enable IS_DEBUG mode for backtests.                 | Boolean | false         |

- [How to set Leverage](https://help.crypto-arsenal.io/en/articles/6572523-how-to-set-leverage)

### Self-defined parameters

User could add their custom parameters and access them through `self['OPTION_NAME']` in the strategy. You can easily change these parameter values for every run of live trade, backtest or simulation.

For example, if you have the following configuration for a strategy

:::caution
All arguments are stored and parsed as string `str` type in your strategy code. **So you be sure to parse to appropriate type yourself!**
:::

#### Type

- Boolean

  A **STRING** that indicates either `true` or `false`

- Number

  A **STRING** that represents a `float` value.

- String

  A **STRING** that holds a `ASCII` string

- Select

  A **STRING** that holds a list of `ASCII` string. Separated by the symbol vertical bar `|`.

#### Example

Suppose you use the following configuration

| Variable | Description  | Type    | Default Value             |
| -------- | ------------ | ------- | ------------------------- |
| MyArgA   | true/false   | Boolean | true                      |
| MyArgB   | a float num  | Number  | 10.9                      |
| MyArgC   | a ASCII Str  | String  | Hello World!              |
| MyArgD   | a ASCII list | Select  | OptionA\|OptionB\|OptionC |

:::note
Only ASCII string is supported currently
:::

Then you're allowed to tweak these variables to be used in your strategy before trading. `MyArgD` will appear as a list consisting of `OptionA`, `OptionB` and `OptionC`.

![image](https://user-images.githubusercontent.com/5862369/56237500-b3511900-60be-11e9-878d-3e5c2cff4991.png)

:::note
You can access these arguments by `self['argName']`
:::

```python
def trade(self, candles):
    CA.log(self['MyArgA']) # true
    CA.log(self['MyArgB']) # 10.9
    CA.log(self['MyArgC']) # Hello World!
    CA.log(self['MyArgD']) # OptionC

    CA.log(str(self['MyArgA'].__class__)) # <class 'str'>
    CA.log(str(self['MyArgB'].__class__)) # <class 'str'>
    CA.log(str(self['MyArgC'].__class__)) # <class 'str'>
    CA.log(str(self['MyArgD'].__class__)) # <class 'str'>

    if self['MyArgB']:
        self.MyArgB = float(self['MyArgB'])
```

:::caution All of the types are string in python

So if you want to check MyArgA is true or not, you have to use it like `if self['MyArgA'] == 'true'` instead of ~~`if self['MyArgA]`~~.

:::
