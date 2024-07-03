---
sidebar_position: 3
sidebar_label: XGBoost
hide_title: false
---

import { Highlight } from "../../../../../src/components/Highlight.js";

# XGBoost

We support XGBoost model with version `xgboost==1.6.1`

Make sure that the model is trained with `xgboost==1.6.1`. Dump the model with `joblib==1.1.0` and upload the pkl to the strategy.

> Learn more about the [strategy flow here](https://help.crypto-arsenal.io/en/articles/6406316-strategy-flow-ml-model)

**Your side**

```py
import joblib

joblib.dump(xgb, 'xgb.pkl')
```

**Crypto Arsenal**

```py
xgb = CA.get_source("my xgb model")
xgb.predict(...)
```


