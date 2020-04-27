# Association-Rule-Mining
Apriori algorithm implementation for association-rule mining (*unsupervised learning*)

## Run
Run `index.html`

## Documentation
### new Apriori(data, [minSupport, minConfidence])
```
let data = [['I1', 'I4', 'I6'], ..., ['I2', 'I4']]
let apriori = new Apriori(data, 10, 0.75)
```
Constructor function <br>
*data* - array2d, each array within data contains a list of items that occured together <br>
*minSupport* (optional) - integer, number that determines what a frequent itemset is <br>
*minConfidence* (optional) - float in range [0;1], determines how often a rule must hold (in percent) to be considered a valid rule

### async getRules() : ruleObject
```
...
let rules = await apriori.getRules()
```
GetRules returns an array of all rules with `confidence > minConfidence`. The array looks like following:
```
rules => 
[
  { rule: [[A], [B]], confidence: (between minConfidence and 1) },
  ...
]
```

## Algorithm

It basically searches for rules that often hold. Consider the rule
```
A -> B
A ... set of items
B ... set of items
```
This means, if all items within set `A` occur, the items in set `B` are likely to occur, too.

Useful articles: 

- https://towardsdatascience.com/association-rules-2-aa9a77241654
- https://towardsdatascience.com/complete-guide-to-association-rules-2-2-c92072b56c84

## Data
A dataset from Kaggle is used: `shopping basket data set` which contains shopping baskets as lists of items in it.

<br> e.g.
```
bottled beer
beef,grapes,fruit/vegetable juice
pip fruit,sugar
root vegetables,onions,other vegetables,yogurt,frozen meals,vinegar,canned vegetables,soda,salty snack,napkins
chicken,beef,citrus fruit,whole milk,cream cheese,domestic eggs,rolls/buns,canned beer,napkins,shopping bags
bottled water
```
