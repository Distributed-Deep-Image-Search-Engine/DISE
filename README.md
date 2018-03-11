# DISE
---
*Deep Image Search Engine*
___

## Experiment#1: Transfer Learning on FashionMNIST

### Specifications
- Architecture: RESNET34
- Dataset: FashionMNIST

### Modus Operandi

- Enable data augmentation and convolutional precomputation for quick iteration
- Use learning rate finder to find highest learning rate where loss is still clearly improving
- Train last layer from precomputed activations for 2 epochs
- Train last layer with data augmentation for 2-3 epochs with cycle_len=1
- Unfreeze all layers and turn off precomputation
- Set earlier layers to 3x-10x lower learning rate than next higher layer
- Find the optimal learning rate again: 0.05
- Train full network with cycle_mult=2 until over-fitting

### Classification Report

```
				precision    recall  f1-score   support  
          0       0.92      0.91      0.91      1023
          1       1.00      0.99      0.99       988
          2       0.90      0.91      0.91      1008
          3       0.94      0.95      0.94      1021
          4       0.91      0.89      0.90      1050
          5       0.99      0.99      0.99       996
          6       0.84      0.85      0.84       970
          7       0.95      0.98      0.97       955
          8       0.99      1.00      0.99       968
          9       0.98      0.96      0.97      1021
	avg/total     0.94      0.94      0.94     10000  
```

**Conclusion**
1. We have a very coherent f1-score, recall and precision: 94%  
2. Some classes like label:1(trousers) have 100% precision and 99% recall
3. The classs with lowest performance is label:6(shirts)



