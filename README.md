# CryptoQuery
Testing simple queries for crypto APIs

You can definitely query the CoinGecko API from the JavaScript console in your browser. Here's a step-by-step guide to get you started:

1. **Open the JavaScript Console:**
   - In most browsers, you can open the console by pressing `F12` or `Ctrl+Shift+I` (Windows) or `Cmd+Option+I` (Mac), and then selecting the "Console" tab.

2. **Use the Fetch API to Make HTTP Requests:**
   - The Fetch API provides an easy way to make HTTP requests from the browser.

3. **Query the CoinGecko API:**
   - Here’s an example of how to use the Fetch API to get the current price of Bitcoin in USD:

```javascript
// Define the API endpoint
const apiUrl = 'https://api.coingecko.com/api/v3/simple/price?ids=bitcoin&vs_currencies=usd';

// Use the Fetch API to make a GET request
fetch(apiUrl)
  .then(response => response.json()) // Parse the JSON from the response
  .then(data => {
    console.log('Bitcoin Price in USD:', data.bitcoin.usd); // Log the price to the console
  })
  .catch(error => {
    console.error('Error fetching data:', error); // Log any errors to the console
  });
```

4. **Customize the Request:**
   - You can customize the `apiUrl` variable to query different coins or currencies. For example, to get the price of Ethereum in EUR:

```javascript
const apiUrl = 'https://api.coingecko.com/api/v3/simple/price?ids=ethereum&vs_currencies=eur';

fetch(apiUrl)
  .then(response => response.json())
  .then(data => {
    console.log('Ethereum Price in EUR:', data.ethereum.eur);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });
```

5. **List All Coins:**
   - To get a list of all coins supported by CoinGecko:

```javascript
const apiUrl = 'https://api.coingecko.com/api/v3/coins/list';

fetch(apiUrl)
  .then(response => response.json())
  .then(data => {
    console.log('List of all supported coins:', data);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });
```

These examples should help you get started with querying the CoinGecko API from the JavaScript console. If you have any more questions or need further assistance, feel free to ask! 😊

You can find more information about the CoinGecko API [here](https://www.coingecko.com/en/api/documentation).
