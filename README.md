# Decision-trees

# 1. Key questions

## a. Which feature to split on each node:
depends on the result in two branches. We have to maximize the purity or minimize the impurity.
## b. When to stop splitting
- a node is 100% one class
- tree exceeds maximum depth
- improvement in purity score is below a threshold
- number of examples is below a threshold

# 2. Entropy and information gain
- entropy used as a measurement of impurity
- at root node, let $p^{root}$ be the fraction of positive cases. Then information gain is
$$H(p^{root})- (w^{left}H(p^{left}) + w^{right}H(p^{right})$$
where $w^{left}, w^{right}$ are the proportion of examples in each subbranch

Improvement in purity is equivalent to the fact that information gain should be as large as possible.
Note
- if a feature is categorical (>=3) then we use one-hot coding, meaning that divide it into smaller features of values 1/0.
- decision tree can be applied to continuous feature, by first sorting then setting thresholds, for each threshold we can count and therefore do the same thing.
# 3. Regression trees
We just need to modify 2 things:
- the results (leaf nodes) now are the average of all the values in that node
- the role of entropy is replaced by variance.

# 4. Tree ensembles
- Basic idea: create a collection of trees by sampling with replacement --> Bagged decision tree (like putting examples in a bag). Repeating sampling $B$ times, $B$ shouldn't be too large, around 100 is enough. Then vote.
- Random forest: at each node, suppose we have $n$ choices, instead of testing through $n$, we only consider random $k < n$. The cases that same features and same split become less.
- XGBoost: rather than sampling with replacement where each example is chosen with equal probability, the idea is for each iteration from 1 to $B$, we look back at previous already built trees to see where they don't do well, spot examples, increase probabilities of chosing these examples in the next step.
