# SVD

分解一个m x n矩阵$D$为三个矩阵相乘：
$$D=USV^T$$
其中$U$（m x m），$V$（n x n）都是单位正交阵，$S$（m x n）是对角阵，对角元素均大于0，排列从大到小

## 反演中的应用
对于反演问题：

$$ \min \left\| {Gm - d} \right\|_2^2 + {\alpha ^2}\left\| {Lm} \right\|_2^2 $$

当L取0阶正则化单位阵$I$时，有：

$$\min \left\| {\left[ {\begin{array}{*{20}{c}}  G \\   {\alpha I} \end{array}} \right]m - \left[ {\begin{array}{*{20}{c}}  d \\   0 \end{array}} \right]} \right\|_2^2$$

对$G$进行SVD分解，最后解为：

$$ {m_\alpha } = \sum\limits_{i = 1}^k {\frac{{s_i^2}}{{s_i^2 + {\alpha ^2}}}\frac{{{{\left( {{U_{.,i}}} \right)}^T}d}}{{{s_i}}}{V_{.,i}}} $$

