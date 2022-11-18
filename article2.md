---

作者：hfc

时间：2022-11-18-14:22

---

## 2.Finite Block-Length Analysis of Large-But-Finite MIMO Systems

- 作者：Behrooz Makki , Tommy Svensson , Mikael Coldrey, and Mohamed-Slim Alouini

- 期刊：IEEE WIRELESS COMMUNICA TIONS LETTERS, VOL. 8, NO. 1, FEBRUARY 2019

- 摘要：本文研究了点对点多输入多输出系统在存在大量但有限数量的发射和接收天线的情况下的性能。我们利用最近关于有限长码可达速率的一些结果来分析在短包情况下的系统性能。给出了不同衰落模型下的计算结果。在码字长度有限的情况下，我们推导了误码率/吞吐量的闭合表达式，并确定了满足不同误码率/吞吐量要求所需的最小天线数。如我们所示，虽然误差约束所需的天线数目对短码字的长度很敏感，但对于中长码字其影响可以忽略不计。
- 关键词—MIMO, finite block-length analysis, throughput.

### 介绍

- 目标是确定满足各种错误概率/吞吐量要求的发射和/或接收天线的所需数量。导出了吞吐量、错误概率以及满足不同QoS要求的最小天线数的闭式表达式（定理1和2）。此外，我们还评估了天线数量、衰落模型和空间相关性等各种参数对系统性能的影响。

### 系统模型

- $N_t$个发射天线，$N_r$个接收天线，码字传输期间信道系数恒定准静态。
  $$
  \bold{Y = HX + Z} \tag{1}
  $$
  其中$\bold{Z} \in \mathcal{C}^{N_r + 1},\bold{H} \in \mathcal{C}^{N_r \times N_t},\bold{X} \in \mathcal{C}^{N_r + 1}$，$\bold{H}$中每个元素$i.i.d$服从$\mathcal{CN}(0,1)$

- 假定接收机已知信道系数，在发射机处没有可用的信道状态信息，$K$个信息$nats$，码长为$L$，速率为
  $$
  R = \frac{K}{L} (npcu) \tag{2}
  $$
  使用正态近似具有各向同性分布码本的系统，解码错误概率$Pr(error)$，错误概率近似为
  $$
  Pr(error) = E\Bigg[Q\bigg(\frac{\sqrt{L}(C(\bold{H}) - R)}{\sqrt{V(\bold{H})}} \bigg) \Bigg] \tag{3}
  $$

  $$
  C(\bold{H}) = \log \bigg|\bold{I}_{N_r} + \frac{P}{N_t}\bold{HH}^h \bigg| \tag{4}
  $$

  $$
  V(\bold{H}) = \min(N_t,N_r) - \sum_{j = 1}^{\min(N_t,N_r)}\frac{1}{(1 + \frac{P}{N}\mathcal{\bar\omega}_j)^2} \tag{5}
  $$

  其中$P(in~dB, 10\log_{10}P)$是总传输功率，因为方差为$1$也代表信噪比。$\bold{I}_{N_r}$代表$N_r \times N_r$的单位矩阵。$\{\mathcal{\bar\omega}_j\},j=1,\cdots,\min(N_t,N_r)$代表$\min(N_t,N_r)$个$\bold{HH}^h$的最大特征值，$(\cdot)^h$是厄米算符。给定的数据速率$R$，系统吞吐量为
  $$
  \eta = R(1 - Pr(error)) \tag{6}
  $$
  由(3-6)可知，吞吐量和错误概率是$Pr(error)$的单调函数，最小所需天线数为
  $$
  \{\hat{N_t}, \hat{N_r} \} = \underset{N_t,N_r}{\arg\min}\{Pr(error) \leq \theta\} \tag{7}
  $$
  其中$\theta$表示错误概率约束，因此$\eta \geq R(1 - \theta)$

- 推导的三种情况

  - Case1：$N_r$很大，$N_t$给定
  - Case2：$N_r$给定，$N_t$很大
  - Case3：$N_r,N_t$很大，$SNR$很小，$c = \frac{N_t}{N_r}$是个常量

- 定理1：由，式(4)收敛于一个等价的高斯随机变量$\mathcal{Y} \sim \mathcal{N}(\mu,\sigma^2)$，其中![image4](article2.assets\image4.png)

  作为二阶近似，这里使用
  $$
  V(\bold{H}) \simeq
  
  \min(N_t,N_r) =
  
  \begin{cases}
  
  N_t,& \quad Case1 \quad or \quad Case3 \quad with \quad c < 1 \\
  
  N_r,& \quad Case2 \quad or \quad Case3 \quad with \quad c \geq 1
  
  \end{cases}\tag{8}
  $$


  因此错误概率$Pr(error)$可以近似为
$$
\begin{aligned}
  Pr(error) &\simeq \int_0^\infty f_{\mathcal{Y}}(y)Q\Bigg(\frac{\sqrt{L}(y - R)}{\sqrt{\min(N_t,N_r)}} \Bigg)dy \\
  & \simeq \int_0^{R - \phi}f_{\mathcal{Y}}(y)dy + \int_{R - \phi}^{R + \phi}f_{\mathcal{Y}}(y)\Big(\frac{1}{2} + \frac{R}{2\phi} - \frac{1}{2\phi} \Big)dy \\
  &=\mathcal{U}(R,L,N_t,N_r,P)
  \end{aligned} \tag{9}
$$

$$
\begin{aligned}
  
  \mathcal{U}(R,L,N_t,N_r,P) = 
  &1 - \mathcal{Q}(-\phi)+\Bigg(\frac{1}{2} + \frac{R}{2\phi} \Bigg)\Big(\mathcal{Q}(-\phi) - \mathcal{Q}(\phi)\Big) \\
  
  &-\frac{1}{2\phi}\Bigg(\frac{\mu}{2}\Big(1 - 2\mathcal{Q}(\phi)\Big) - \frac{\sigma}{\sqrt{2\pi}}\exp{\Big(-\frac{\mathcal{Q}^2(\phi)}{2\sigma^2}\Big)}\\
  
  &-\frac{\mu}{2}\Big(1 - 2\mathcal{Q}(-\phi)\Big) +\frac{\sigma}{\sqrt{2\pi}}\exp{\Big(-\frac{\mathcal{Q}^2(-\phi)}{2\sigma^2}\Big)}\Bigg)
  
  \end{aligned} \tag{10}
$$

  其中$\mathcal{Q}(\phi) = Q(\frac{R + \phi - \mu}{\sigma})$，$\phi = \frac{\sqrt{\pi\min(N_t,N_r)}}{2L}$，式(9)根据下式化简
$$
F_{\mathcal{Y}}(y) = 1 - Q(\frac{y - \mu}{\sigma}) \\
  Q\Bigg(\frac{\sqrt{L}(y - R)}{\sqrt{\min(N_t,N_r)}} \Bigg) \simeq \mathcal{V}(y)\\ \tag{11}
$$
  ![image5](article2.assets\image5.png)

- 当$N_r,N_t$逐渐增大时，由(3)、(8)和(8)上面的等式可得

  ![image6](article2.assets\image6.png)

  根据上式可得，在给定$N_r$的概率下，随着发射天线数量的增加，错误概率(几乎)与发射天线数量无关