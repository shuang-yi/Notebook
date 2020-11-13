$x_k\;(k\in S)$

Suppose a time series of $N_1$ contains $N_2$ data gaps  (denoted by a set $S$). The complete time series $\boldsymbol{X}$ consists of $x_i \;(i \in [1, N=N_1+N_2])$ . The trajectory matrix $\mathbf{C}$ (also known as Toeplitz lagged correlation matrix) of the series under a window size $L$ is formulated by
$$
\mathbf{C}=\begin{bmatrix} 
c(0) & c(1) & \cdots & c(L-1) \\ 
c(1) & c(0) & \cdots & \vdots \\ 
\vdots & \vdots & \ddots & c(1) \\ 
c(L-1) & c(L-2) & \cdots & c(0) 
\end{bmatrix},
$$
where
$$
c(j)=\frac{1}{N_j}\sum_{i+j\le N, i+j\notin S}{x_ix_{i+j}}\quad(j\in[0,L-1]).
$$
The eigenvectors $\boldsymbol{\nu}_k\;(k\in [1,L])$ of the matrix $\mathbf{C}$ are solved and arranged in the descending order of their associated eigenvalues $\lambda_k$. 

The *k*th corresponding principle component (PC) is 
$$
A_k=\mathbf{V}_k\boldsymbol{X},
$$

$$
\mathbf{V}_{k}=\begin{bmatrix} 
\nu_{k,1} & \nu_{k,2} & \cdots & \nu_{k,L} & 0 & \cdots & 0 \\ 
0 & \nu_{k,1} & \cdots & \nu_{k,L-1} & \nu_{k,L} & \cdots & 0 \\ 
\vdots & \vdots & \ddots & \vdots & \vdots & \ddots &\vdots \\ 
0 & 0 & \cdots & \nu_{k,1} & \nu_{k,2} & \cdots & \nu_{k,L} \\ 
\end{bmatrix}
$$

 
$$
w_{i,i}=\begin{cases}
      1/i, & i<L \\
      1/L, & \text{otherwise} \\
      1/(N-L-i), & i>N-L
    \end{cases}
$$
