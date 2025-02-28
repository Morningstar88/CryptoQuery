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

NOTE: FOLLOWING BOTS MOSTLY WORK OFF THE BAT< EXCEPT NEWS.

Sure thing! Here are some fun mini-bots for JavaScript beginners that use the CoinGecko API. These scripts are great for learning and experimenting with API interactions:

### 1. **Crypto Price Checker**
This bot fetches the current price of a specified cryptocurrency and logs it to the console.

```javascript
const apiUrl = 'https://api.coingecko.com/api/v3/simple/price?ids=bitcoin&vs_currencies=usd';

fetch(apiUrl)
  .then(response => response.json())
  .then(data => {
    console.log('Bitcoin Price in USD:', data.bitcoin.usd);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });
```

### 2. **Top Gainers and Losers**
This bot fetches the top gainers and losers in the cryptocurrency market.

```javascript
const apiUrl = 'https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=10&page=1&sparkline=false';

fetch(apiUrl)
  .then(response => response.json())
  .then(data => {
    const gainers = data.sort((a, b) => b.price_change_percentage_24h - a.price_change_percentage_24h).slice(0, 5);
    const losers = data.sort((a, b) => a.price_change_percentage_24h - b.price_change_percentage_24h).slice(0, 5);

    console.log('Top 5 Gainers:', gainers);
    console.log('Top 5 Losers:', losers);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });
```

### 3. **Crypto Market Cap**
This bot fetches the market capitalization of a specified cryptocurrency.

```javascript
const apiUrl = 'https://api.coingecko.com/api/v3/coins/bitcoin';

fetch(apiUrl)
  .then(response => response.json())
  .then(data => {
    console.log('Bitcoin Market Cap:', data.market_data.market_cap.usd);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });
```

### 4. **Crypto News Fetcher**
This bot fetches the latest news articles related to cryptocurrencies.

```javascript
const apiUrl = 'https://api.coingecko.com/api/v3/news';

fetch(apiUrl)
  .then(response => response.json())
  .then(data => {
    console.log('Latest Crypto News:', data);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });
```

### 5. **Crypto Portfolio Tracker**
This bot tracks the value of a simple crypto portfolio.

```javascript
const portfolio = {
  bitcoin: 0.5,
  ethereum: 2,
  litecoin: 10
};

const apiUrl = 'https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,litecoin&vs_currencies=usd';

fetch(apiUrl)
  .then(response => response.json())
  .then(data => {
    const totalValue = Object.keys(portfolio).reduce((acc, coin) => {
      return acc + (portfolio[coin] * data[coin].usd);
    }, 0);

    console.log('Total Portfolio Value in USD:', totalValue);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });
```

These scripts should give you a good starting point for building your own mini-bots using the CoinGecko API. Have fun experimenting and learning! 😊

You can find more information on building bots with the CoinGecko API [here](https://www.coingecko.com/learn/ai-crypto-chatbot).

Sure, I'd be happy to walk you through the logic and steps for a bot that buys a cryptocurrency and sells it when the price doubles. Here's a high-level overview of how such a bot might work:

### 1. **Initialize Settings and Variables:**
   - Define the initial investment amount.
   - Select the cryptocurrency to buy.
   - Set the target sell price (e.g., double the buy price).
   - Initialize a variable to track the state (whether the bot currently holds the coin or not).

### 2. **Connect to the API:**
   - Connect to a cryptocurrency exchange API (e.g., CoinGecko, Binance) to fetch real-time price data.
   - Set up authentication if required by the exchange API.

### 3. **Fetch Current Price:**
   - Periodically fetch the current price of the selected cryptocurrency using the API.

### 4. **Buy Logic:**
   - Check if the bot does not currently hold the coin.
   - Fetch the current price and compare it with the initial investment amount.
   - If conditions are met, execute a buy order:
     - Store the buy price.
     - Update the state to indicate that the bot now holds the coin.

### 5. **Track Price:**
   - Continuously monitor the current price of the cryptocurrency.
   - Calculate the target sell price based on the buy price (e.g., double the buy price).

### 6. **Sell Logic:**
   - Check if the bot currently holds the coin.
   - Fetch the current price and compare it with the target sell price.
   - If the current price is equal to or greater than the target sell price, execute a sell order:
     - Calculate and log the profit.
     - Update the state to indicate that the bot no longer holds the coin.

### 7. **Handle Errors and Exceptions:**
   - Implement error handling for API connectivity issues, invalid responses, or unexpected conditions.
   - Include logging for errors and successful transactions.

### 8. **Optimization and Improvements:**
   - Consider implementing additional features like dynamic buy/sell thresholds, risk management, and multiple currency support.
   - Optimize the frequency of price checks to balance between responsiveness and API rate limits.

### 9. **Security:**
   - Ensure that API keys and sensitive information are securely stored and managed.
   - Implement safety checks to avoid executing unintended trades.

### 10. **Testing and Deployment:**
   - Thoroughly test the bot in a simulated environment to ensure that it behaves as expected.
   - Deploy the bot to run on a server or cloud platform for continuous operation.

These steps should provide a solid foundation for creating a cryptocurrency trading bot that buys a coin and sells it when the price doubles. If you need help with specific aspects or have any other questions, feel free to ask! 😊
