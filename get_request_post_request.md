---
sidebar_position: 17
sidebar_label: get_request / post_request
hide_title: false
---

import { Highlight } from "../../../../../src/components/Highlight.js";

# get_request / post_request

<Highlight color="#ffba00"> Using `get_request`, `post_request` in backtest is not recommended. </Highlight>

## Input

- get_request
```typescript
url
params: {key: value}
args
```

- post_request
```
url
data: {key: value}
json: {key: value}
args
```

Supported URLs (Third party APIs):

| Website | API Endpoints | API Documentation |
| - | - | - |
| [Etherscan](https://etherscan.io/) | https://api.etherscan.io/ | https://docs.etherscan.io/ |
| [Glassnode](https://glassnode.com/) | https://api.glassnode.com/ | https://docs.glassnode.com/ |
| [CryptoQuant](https://cryptoquant.com/) | https://api.cryptoquant.com/ | https://cryptoquant.com/docs |
| [Twitter](https://twitter.com/) | https://api.twitter.com/ | https://developer.twitter.com/en/docs/twitter-api |
| [APILayer](https://apilayer.com/) | https://api.apilayer.com | https://apilayer.com/docs |
| [Luabase](https://luabase.com/) | https://api.luabase.com/ | https://luabase.notion.site/Luabase-Docs-e9c2c5338c47494cb35294b47ce4b744 |
| [Santiment](https://santiment.net/) | https://santiment.net/ | https://academy.santiment.net/ |


## Example

```
  url = "https://api.apilayer.com/currency_data/live?source=USD&currencies=EUR"
  payload = {}
  headers= {
    "apikey": "[YOUR_API_KEY]"
  }
  response = CA.get_request(url, headers=headers, data=payload)

  status_code = response.status_code
  result = response.json()
  CA.log(str(status_code))
  CA.log(str(result))
  CA.log(str(result['quotes']['USDEUR']))
```

logging:

```
200
{'success': True, 'timestamp': 1655851923, 'source': 'USD', 'quotes': {'USDEUR': 0.948897}}
0.948897
```
