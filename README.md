# Automated Option Chain Analysis and Margin Calculation for Financial Instruments

## Overview  
This project simplifies option trading analysis by automating the retrieval and evaluation of option chain data using the Upstox API. It calculates the highest bid or ask prices for various strike prices and determines the margin required and premium earned for selling options.  

## Features  
1. **Automated Data Retrieval**: Extract option chain data with key details like strike prices, bid/ask prices, and instrument keys.  
2. **Margin and Premium Calculation**: Use the Upstox margin API to calculate the required margin and premium for selling options.  
3. **Streamlined Workflow**: Separate functions for option data retrieval and margin/premium calculations for clarity and reusability.  

---

## Code Structure  

### Function 1: `get_option_chain`  
- **Purpose**: Fetch option chain data for a specified instrument and expiry date.  
- **Functionality**:  
  - Identifies the **highest bid price** for Put Options (PE) or **highest ask price** for Call Options (CE) for each strike price.  
  - Outputs a row of critical data with columns like:  
    - `instrument_name`: Name of the financial instrument (e.g., NIFTY).  
    - `strike_price`: Strike price of the option.  
    - `side`: "PE" for put options or "CE" for call options.  
    - `bid_or_ask`: Highest bid (PE) or ask (CE) price.  
    - `instrument_key`: Unique identifier required for margin calculation.  

### Function 2: `calculate_margin_premium`  
- **Purpose**: Compute the **margin required** and **premium earned** for selling options.  
- **Functionality**:  
  - Calls the **Upstox margin API** with `instrument_key` and quantity (lot size).  
  - Calculates:  
    - **Margin Required**: API-provided margin for option selling.  
    - **Premium Earned**: Product of `bid_or_ask` price and lot size.  
  - Outputs enhanced data with `margin_required` and `premium_earned`.  

---

## Approach  

### Key Highlights  
- **Efficiency**: Leveraged modular functions to ensure clarity and ease of integration with Upstox APIs.  
- **Enhanced Data Handling**: Included `instrument_key` to bridge option data with margin calculations seamlessly.  
- **Real-Time Calculations**: Ensures accurate and instant margin and premium evaluations.  

### Challenges Overcome  
- Extracting precise data from complex API responses (e.g., JSON parsing).  
- Managing multiple API calls in real time while ensuring data consistency.  

---

## Usage  

1. **Setup**: Configure your `client_id`, `secret_key`, and `redirect_uri` for Upstox API authentication.  
2. **Step 1**: Run `get_option_chain` to retrieve option data for a chosen instrument and expiry date.  
3. **Step 2**: Pass the resulting DataFrame to `calculate_margin_premium`, specifying the lot size.  

---

This project offers a robust and automated solution for analyzing option chain data and calculating key trading metrics, making it an invaluable tool for traders.  
