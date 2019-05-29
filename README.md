# Perceptron
Implemented the perceptron algorithm


## 1.Main codes

```python

def perceptron(train_ys, train_xs, dev_ys, dev_xs, args):
    weights = np.zeros(NUM_FEATURES)
    N = len(train_xs)
    epoch = N/5
    bestDevWeights = weights
    bestAccuracy = 0
    for i in range(args.iterations):
        for n in range(N):
            if np.dot(weights, train_xs[n])*train_ys[n] <= 0:
                weights += (args.lr * train_xs[n] * train_ys[n])
                if not args.nodev and n%epoch == 0:
                    currentAccuracy = test_accuracy(weights, dev_ys, dev_xs)
                    if  currentAccuracy > bestAccuracy:
                        bestAccuracy = currentAccuracy
                        bestDevWeights = weights
    
    
```

## 2.Performance changes with number of iterations increases

accuracy/Number of iterations: 

0.7856045384706299 / 1

0.8171610920694953 / 2

0.7826498049875901 / 4

0.807351376905803  / 8

0.7769767167001537 / 16



## 3.How to best use dev data during training.

Here I added a variable "epoch" whose value is N/5. For each epoch, I will call test_accuracy to check the goodness of the weights. If the current epoch's accuracy is bigger than the best, I will updated it using current's weights.


## 4.Performance changes with learning rate

accuracy/learning rate: 

0.7840680770594493 / 0.01

0.8051057794586928 / 0.05

0.8051057794586928 / 0.1

0.8171610920694953 / 0.5

0.8171610920694953 / 1

0.8171610920694953 / 2

0.8171610920694953 / 5
