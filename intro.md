---
sidebar_position: 1
sidebar_label: Introduction
hide_title: false
---

# Introduction

export const Highlight = ({ children, color }) => (
  <span
    style={{
      backgroundColor: color,
      borderRadius: "2px",
      color: "#fff",
      padding: "0.2rem",
    }}
  >
    {children}
  </span>
);

import Tabs from "@theme/Tabs";
import TabItem from "@theme/TabItem";

### Tutorial

<Tabs
  defaultValue="developer"
  values={[
    { label: "Strategy Developer 👩‍💻", value: "developer" },
    { label: "Trader 💵", value: "trader" },
  ]}
>
  <TabItem value="developer">

[Develop in Python](/docs/developer/get-started/python/hello-world)

  </TabItem>
  <TabItem value="trader">

:::note
We are working hard on this 👷
:::

  </TabItem>
</Tabs>

### Overview

![](https://crypto-arsenal.io/static/howtostart-zh-TW.svg)
