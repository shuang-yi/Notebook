#傅里叶展开
傅里叶级数一般形式
$f\left( x \right) = \frac{{a_0}}{{2}} + \sum\limits_{n = 1}^\infty  {\left( {{a_n}\cos nx + {b_n}\sin nx} \right)} $
$\int\limits_{ - \pi }^\pi  {\frac{a_0}{2}dx}  = \pi {a_0} = \int\limits_{ - \pi }^\pi  {f\left( x \right)dx} $
$\int\limits_{ - \pi }^\pi  {{a_n}\cos nx\cos nxdx}  = \pi {a_n} = \int\limits_{ - \pi }^\pi  {f\left( x \right)\cos nxdx} $

傅里叶级数指数形式
$f\left( x \right) = \sum\limits_{ - N}^N {{c_n}{e^{inx}}} $
${c_n} = \left\{ {\begin{array}{*{20}{c}}
{\left( {{a_n} - i{b_n}} \right)/2}&{,n > 0}\\
{{a_0}/2}&{,n = 0}\\
{\left( {{a_n} + i{b_n}} \right)/2}&{,n < 0}
\end{array}} \right.$

${{c}_{n}}=\frac{1}{2}\int\limits_{-\pi }^{\pi }{f\left( x \right){{e}^{-inx}}dx}$

# FFT
Y = fft(X,n,dim)

## Foward Discrete Fourier Transform (DFT)
${X_k} = \sum\limits_{n = 0}^{N - 1} {{x_n}{e^{ - i2\pi kn/N}}}$

Inverse Discrete Fourier Transform (IDFT)
${x_n} = \frac{1}{N}\sum\limits_{k = 0}^{N - 1} {{X_k}{e^{i2\pi kn/N}}}$


