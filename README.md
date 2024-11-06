# Crypto Metrics

## Introduction

**Crypto Metrics API** provides cryptocurrency metrics including volume, highs, lows and much more.

## Authentication

The URL you need to use is the following: `https://crypto-metrics.p.rapidapi.com/`
The API requires the headers listed below:

- **`x-rapidapi-host`**: `crypto-metrics.p.rapidapi.com`
- **`x-rapidapi-key`**: `YOUR_API_KEY`

Make sure to replace `YOUR_API_KEY` with your API key. You can register one [here](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/crypto-metrics/pricing).
Some frameworks automatically add extra headers, you have to make sure to remove them in order to get a response from the API.

## Endpoints

The API is configured to accept only **GET** requests. Below are the available endpoints with their descriptions and required parameters.

### 1. **`GET /coin-metrics/:cryptoISO`**

- **Description**: Retrieves crypto metrics by crypto currency.

| Path Parameter | Type   | Default | Description                                 | Required |
|----------------|--------|---------|---------------------------------------------|----------|
| `cryptoISO`    | string | -       | The ISO of the crypto to search for         | Yes      |

Example request:

```javascript
fetch('https://crypto-metrics.p.rapidapi.com/coin-metrics/ETH', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'crypto-metrics.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "eVol24h": "22703565702",
  "eVol30d": "471698982606",
  "cVol24h": null,
  "cVol30d": null,
  "txCnt24h": 1173025,
  "txCnt30d": 34802973,
  "txFees24h": 4407215.100029,
  "txFees30d": 137899181.167036,
  "txFeesMean24h": 3.757137,
  "cVolAdj24h": null,
  "ret24h": 0.029388,
  "retMTD": 0.04384,
  "retQTD": 0.04384,
  "retYTD": 0.190558,
  "retY1": 0.49281,
  "retY3": -0.370718,
  "retY5": 13.966665,
  "retSI": 347.017103,
  "volat30d": 0.489484,
  "low52w": 1779.1488,
  "high52w": 4092.896526,
  "splyCurr": 120406284.163316,
  "splyTotal": 120406284.163316,
  "splyMax": null,
  "ath": 4865.572397,
  "ts": 1730299152873,
  "src": "tb",
  "category": "Software platform",
  "type": "Global computer",
  ...
```

### 2. **`GET /coin-metrics`**

- **Description**: Retrieves all coin metrics.

Example request:

```javascript
fetch('https://crypto-metrics.p.rapidapi.com/coin-metrics', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'crypto-metrics.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "statusCode": 200,
  "message": "OK",
  "data": {
    "BTC": {
      "eVol24h": "45778259185",
      "eVol30d": "972991984500",
      "cVol24h": null,
      "cVol30d": null,
      "txCnt24h": 617786,
      "txCnt30d": 19834199,
      "txFees24h": 834979.938342,
      "txFees30d": 42605667.787935,
      "txFeesMean24h": 1.351825,
      "cVolAdj24h": null,
      "ret24h": -0.005362,
      "retMTD": 0.142252,
      "retQTD": 0.142252,
      "retYTD": 0.711607,
      "retY1": 1.086022,
      "retY3": 0.17434,
      "retY5": 6.99613,
      "retSI": 219.068494,
      "volat30d": 0.394884,
      "low52w": 34125.732361,
      "high52w": 73798.248388,
      "splyCurr": 19775284,
      "splyTotal": 21000000,
      "splyMax": 21000000,
      "ath": 73798.248388,
      ...
```

## Error Handling

The  API returns standard HTTP status codes to indicate the success or failure of API requests. Below are common errors and suggestions for handling them.

|Status Code|Message|Description|Suggested Handling|
|--|--|--|--|
| **400** | Bad Request | The request was malformed or missing required parameters (e.g., `domain` parameter not provided). | Verify that all required parameters are included and correctly formatted. |
| **401** | Unauthorized | Invalid or missing API key in the request headers. | Check that a valid API key is included in `x-rapidapi-key`. |
| **403** | Forbidden | Access to the requested resource is denied, possibly due to rate limits or restricted access. | Review rate limits and ensure API permissions. Retry after a delay if rate limit exceeded. |
| **404** | Not Found | The requested domain information could not be found (e.g., domain does not exist). | Check the spelling or availability of the domain. |
| **429** | Too Many Requests | The API rate limit has been exceeded. | Implement rate-limiting logic and retry after the specified rate limit reset time. |
| **500** | Internal Server Error | A server error occurred while processing the request. | Retry the request after a few seconds. If the error persists, contact API support. |
| **503** | Service Unavailable | The API service is temporarily unavailable (e.g., due to maintenance). | Retry the request later or check the API status page for maintenance alerts. |

