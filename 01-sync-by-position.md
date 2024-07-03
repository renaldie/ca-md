import Image from "@theme/IdealImage";

# Sync By Position

> Easiest Way to connect - Copy and Paste once & does NOT require Pinescript editing

#### Step 1: Visit [Strategy](https://crypto-arsenal.io/strategies). Then click on `New Strategy`.

![An image from the static](/img/developer/tradingview/2023-06-23-15-33-01.png)

#### Step 2: Pick your `Exchange` and `Market`. Adjust `Leverage` if you are trading Futures.

![An image from the static](/img/developer/tradingview/2023-06-23-15-36-29.png)

#### Step 3: Click on `TradingView`.

![An image from the static](/img/developer/tradingview/2023-06-23-15-36-39.png)

#### Step 4: Click on `Sync By Position`.

![An image from the static](/img/developer/tradingview/2023-06-23-15-36-46.png)

#### Step 5: Click on `Lock` to edit and set up how you want to enter a trade.

![An image from the static](/img/developer/tradingview/2023-06-23-15-37-14.png)

#### Step 6: Expand `Entry Order Mode` to see supported modes.

- **`Strategy Order Size`:** Place orders with base asset amount based on TradingView strategy's Order Size.

  <details>
    <summary>See Example</summary>
    <h4> We will sync the exact contract size from TradingView strategy </h4>
    <img src="/img/developer/tradingview/2023-06-23-16-20-32.png" />
  </details>

- **`Fixed Quote Amount`:** Trade a fixed quote amount (entry value). _E.g., an entry value of 100U opens a position worth 100U._
- **`Fixed Base Amount`:** Trade a fixed base asset amount (entry value). _E.g., an entry value of 1ETH opens a position worth 1ETH._
- **`Percentage of Balance with Compounding`:** Trade a percentage (entry value) of your balance, including profits. _E.g., with 100U, a 10% trade uses 10U, and the next 10% trade uses 9U from the remaining 90U._
- **`Percentage of Initial Balance Only`:** Trade a percentage (entry value) of your initial balance, excluding profits. _E.g., with 100U, even if it grows to 130U, a 10% trade uses 10U, based on the initial 100U._
- **`Percentage of Balance at No Position`:** When adding to a position, use a percentage (entry value) of your total balance when no position is open. _E.g., with 100U (no position), entering 10% and another 20% uses 10U and 20U._
- **`Strategy Percentage with Fixed Capital`:** Use a fixed capital amount (entry value) to calculate the investment percentage. This could be the equity of your TradingView strategy or a fixed investment amount.

![An image from the static](/img/developer/tradingview/2023-06-23-15-37-23.png)

#### Step 7: Copy and Paste the Message to TradingView Alert Message Box

See How To Set Up TradingView Alert Webhook

<h4> Copy and Paste Webhook URL to Alert > Notification > Webhook URL field</h4>
<img src="/img/developer/tradingview/2023-06-23-16-41-35.png" />

![An image from the static](/img/developer/tradingview/2023-06-23-16-35-59.png)

#### Step 8: Click the card to view and edit settings & Run a Simulation to start testing

![An image from the static](/img/developer/tradingview/2023-06-23-16-47-12.png)
