# Knight Squad Shop
### 100 Points

## Information


Challenge Link : http://206.189.236.145:3000/

Download Links:
 1. <a href="https://drive.google.com/file/d/1cHCasWHdfl21q2XrATET_jy0fDQ2gfMK/view?usp=sharing">Link 1 </a>
 2. <a href="https://drive.google.com/file/d/1Z7lgxlVWvMJaS_C4oDZHSwlVazGjlGw_/view?usp=sharing">Link 2 </a>
 3. <a href="https://drive.google.com/file/d/1qHJdxiyjiY0CaHFDdOqQFQCLAKc9Fo6u/view?usp=sharing">Link 3 </a>

Flag Format : BDSEC{fl4g_h3r3}


## Steps done

1. We visited the URL, and it gift the user $100 to buy products, and exist one product called flag without stock.
2. We tried to buy the flag and received the response  `451 not enough product`
3. We downloaded the code. It consist on:
    - `index.js` file: Express server
    - flag.txt: text file, description of product flag.
   
   We observed on the index.js that import a JSON file called `products.json` and add a product called `flags` with price = 2.5e+25 (25,000,000,000,000,000,000,000,000). And the file has 4 endpoints:
    - GET /: returns the index file with the list of products and the money available in the session (100 initially)
    - POST /api/v1/sell: allows to assign properties to a product and if the entrie has the key quantity add it to the current stock. If the product name is `flag` only can be updated if `req.session.admin == true``
    - POST /api/v1/buy: endpoint to buy one product check if the money if enough returns the product otherwise return `402 not enough money` is the money is not enough or `451 not enough product` if the product stock is not enough
    - POST /api/v1/money: if the `session.admin` is true allows the user to add money otherwise returns `403 not admin``

   The flag `session.admin` it's true if `req.ip == 127.0.0.1` and according to <a href="https://expressjs.com/en/api.html#req.ip ">Express documentation</a> it takes the left-most entry in the `X-Forwarded-For` `header
4. Based on the previous item we sent a POST to `/api/v1/sell` with the header `X-Forwarded-For:127.0.0.1` and the payload `{"flags": {"quantity":1000}}`
5. We tried to buy again the product flag, sending a POST to api/v1/buy and received the response `402 not enough money`
6. We added money sending a POST to `api/v1/money` with the header `X-Forwarded-For:127.0.0.1` and the payload `{"money":3e+25}` and received a sucessfully response
7.  We tried to buy again the product flag, sending a POST to api/v1/buy and received the flag on the response `BDSEC{H3@D3R_1NJ3CT10N}`
    

    