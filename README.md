## Kata: Checkout

We’ll implement the code for a checkout system that handles pricing schemes such as 
* apples cost .5 cents each
* 3 apples cost $1.30 
* buy two, get one free
* Price not found
* Manual price intervention 

In a normal store, things are identified using Stock Keeping Units, or SKUs. In our store, 
we’ll use individual letters of the alphabet (A, B, C, and so on). Our goods are priced individually. 
In addition, some items are multipriced: buy n of them, and they’ll cost you y cents. 
For example, item ‘A’ might cost $5 cents individually, but this week we have a 
special offer: buy three ‘A’s and they’ll cost you $1.30. In fact this week’s prices are:

## 

| Item | Unit Price | Special Price |
| :---: | :---: | :---: |
| A | $0.50 | 3 for $1.30 |
| B | $3 | 2 for $4.5 |
| C | $2 | buy 2 get 1 free |
| D | $1.5 |  |
	
Our checkout accepts items in any order, so that if we scan a B, an A, and another B, we’ll recognize the two B’s and 
price them at $4.5 (for a total price so far of $5). Because the pricing changes frequently, we need to be able to pass 
in a set of pricing rules each time we start handling a checkout transaction.	
```

co = CheckOut.new(pricing_rules)
co.scan(item)
co.scan(item)
    :    :
price = co.total

```
## Examples
| Scan  | Price | Total |
| :---: | :---: | :---: |
|  unknown | 0 |  |
| A | $0.50 | $0.50 |
| AB | $0.50 + $3| $3.50 |
| CDBA | $2 + $1.5 + $3 $.5 | $7 |
| AAAAAA | $1.3 + $1.3 | $2.6 |
| AAACC | $1.3 + $4 | $5.3 |
| AAACCC | $1.3 + $4 | $5.3 |


## More questions
The challenge description doesn’t mention the format of the pricing rules. 
* How can these be specified in such a way that the checkout doesn’t know about 
particular items and their pricing strategies? 
* How can we make the design 
flexible enough so that we can add new styles of pricing rule in the future?