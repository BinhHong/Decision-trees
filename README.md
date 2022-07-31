# Decision-trees

# 1. Key questions

## a. Which feature to split on each node:
depends on the result in two branches. We have to maximize the purity or minimize the impurity.
## b. When to stop splitting
- a node is 100% one class
- tree exceeds maximum depth
- improvement in purity score is below a threshold
- number of examples is below a threshold

# 2. Entropy
used as a measurement of impurity
