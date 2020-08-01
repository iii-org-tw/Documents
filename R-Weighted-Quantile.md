# R wtd.quantile
**wtd.quantile (x, weight=NULL, probs = c(0, .25, .5, .75, 1), normwt=FALSE, na.rm = TRUE)**  

Compute the weighted q-th quantile of the data.  

**Formula**    
Given an ordered sample ![formula](https://render.githubusercontent.com/render/math?math=X_1\le\X_2\le\cdot\cdot\cdot\le\X_n) with respective weights ![formula](https://render.githubusercontent.com/render/math?math=W_1,\W_2,\cdot\cdot\cdot,\W_n.)   
Define:  
![formula](https://render.githubusercontent.com/render/math?math=S_k=(k-1)W_k%2B(N-1)\sum_{i=1}^{k-1}W_i)
For an interpolation of quantile ![formula](https://render.githubusercontent.com/render/math?math=p), find ![formula](https://render.githubusercontent.com/render/math?math=k) such that ![formula](https://render.githubusercontent.com/render/math?math=\frac{S_k}{S_n}\le\p\le\frac{S_{k%2B1}}{S_n}). 
Our estimate would then be: ![formula](https://render.githubusercontent.com/render/math?math=X_k%2B(X_{k%2B1}-X_k)\frac{pS_n-S_k}{S_{k%2B1}-S_k})  
[Source](https://stats.stackexchange.com/questions/13169/defining-quantiles-over-a-weighted-sample)

**Parameters**

- **x :**  
    Vector of data, same length as weight.
- **weight :**  
    Vector of weights, same length as data.
- **probs :**  
    Quantile or sequence of quantiles to compute, which must be between 0 and 1 inclusive.
- **normwt**  
    Weather to normalize weight to 1.
- **na.rm :**  
    Logical: Should NAs be stripped before computation proceeds?


**Returns**  
    Returns an empirical q quantile from a weighted sample.
    
**Examples**
```sh
>>> require(Hmisc)
>>> data <- c(1, 2, 3)
>>> weights<- c(3, 2, 1)
>>> wtd.quantile(data, probs=0.5, weights=weights)
50%
1.5
>>> probs = c(0.1, 0.5, 0.7)
>>> wtd.quantile(data, probs=probs, weights=weights)
10% 50% 70% 
1.0 1.5 2.0
>>> w_equal <- c(1, 1, 1)
>>> wtd.quantile(data, probs=probs, weights=weights) == wtd.quantile(data, probs=probs, weights=w_equal)
TRUE
```
