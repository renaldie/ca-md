---
sidebar_position: 3
sidebar_label: Sklearn
hide_title: false
---

import { Highlight } from "../../../../../src/components/Highlight.js";

# Sklearn

We support Sklearn model with version `sciket-learn==1.0.2`

Make sure that the model is trained with `sciket-learn==1.0.2` Dump the model with `joblib==1.1.0` and upload the pkl to the strategy.

> Learn more about the [strategy flow here](https://help.crypto-arsenal.io/en/articles/6406316-strategy-flow-ml-model)

**Your side**

```py
import joblib

joblib.dump(model, 'model.pkl')
```

**Crypto Arsenal**

```py
model = CA.get_source("my first model")
model.predict(...)
```


