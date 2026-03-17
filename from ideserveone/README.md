- **《Scalable and Unconditionally Secure Multiparty Computation》**, CRYPTO 2007  
  DN 协议提出。在诚实大多数场景下：
  - 半诚实安全可容忍 $t < n/2$，总复杂度为 $O(nC)k$$$；
  - 恶意安全可容忍 $t < n/3$，复杂度为
  $O(nC)k + O(Dn^2)k + \mathrm{poly}(n,\kappa)$.
  这篇工作的核心意义在于，将与电路规模相关的通信复杂度降到了关于参与方数量 $n$ 的线性级别，成为后续诚实大多数高效 MPC 的经典基线。

- **《Perfectly Secure Multiparty Computation and the Computational Overhead of Cryptography》**, EUROCRYPT 2010  
  研究诚实大多数下的恶意安全、完美安全 MPC，并满足 GOD（Guaranteed Output Delivery）性质。  
  该工作实现了**某个严格小于 $1/3$ 的常数比例腐化门限**，而不是直接达到最优的 $ t<n/3 $。  
  其复杂度可写为 $ O(\log^2 n \log s \log d \cdot s) + d \log d \cdot \mathrm{poly}(n, \log s).$
  相比此前要么只能做到计算安全、复杂度为 $\mathrm{poly}(n,k,d,\log s)$，要么做到完美安全但开销为 $n\cdot\mathrm{poly}\log n$，
  这篇工作的重要贡献在于：在完美安全的前提下，将额外开销压缩到接近 polylog 级别。  
  核心技术是利用 **Packed Secret Sharing (PSS)** 对门进行批量处理，并借助 **Benes 网络**实现高效的数据重排。

- **《Near-Linear Unconditionally-Secure Multiparty Computation with a Dishonest Minority》**, CRYPTO 2012  
  研究诚实大多数下的恶意安全、完美安全 MPC，并可容忍 $t < n/2$。  
  该工作将此前每个乘法门大约 $O(n^2\kappa)$ 比特的通信复杂度，降低到了接近 $O(n \log n)$ 的量级。  
  其总复杂度为
  $ O(c_M(n\phi+\kappa) + d_M n^2 \kappa + n^7\kappa),$ 
  其中主要思想是**批量验证（batch verification）**，从而显著降低乘法验证的摊销。

- **《Guaranteed Output Delivery Comes Free in Honest Majority》**, CRYPTO 2020  
  研究诚实大多数下的**恶意安全**协议，并实现 **GOD** 性质。  
  该工作没有沿用《Near-Linear》那条基于 Beaver triple 批量验证的路线，而是在 DN 协议框架下实现了 $O(Cn\phi)$ 的总复杂度， $\phi$ 是域元素长度。  
  具体到每个乘法门的通信复杂度可做到 best case下 $5.5+\varepsilon$ 和 worst case 下 $7.5+\varepsilon$ 个域元素。  
  这篇工作的核心意义在于：在诚实大多数场景下，证明了实现 GOD 所需的额外代价其实可以非常小，几乎“免费”。

- **《Unconditional Communication-Efficient MPC via Hall’s Marriage Theorem》**, CRYPTO 2021  
  该工作实现了：半诚实情况下的完美安全和带中止（with abort）的恶意情况下的统计安全。  
  每个乘法门的通信复杂度为 $O(n/k),$ 其中 $k$ 为域元素比特长度。  
  技术核心是通过 **Packed Secret Sharing (PSS)** 批量计算一层乘法门，并利用图论中的 **Hall’s Marriage Theorem** 完成数据对齐。  
  这篇工作通过牺牲一定的腐化门限，在单个算术电路上实现了非常低的逐门通信复杂度。

- **《Atlas: Efficient and Scalable MPC in the Honest Majority Setting》**, CRYPTO 2021  
  这篇工作主要是对 DN 协议做进一步优化。  
  在半诚实场景下，它将 DN 协议中每个乘法门需要的通信量从 **6 个域元素**降到了 **4 个域元素**。这一改进也可以继承到恶意安全版本中。  
  此外，它还提出了两层乘法门并行化的方法：每个门额外增加 $0.5$ 个元素的代价，就可以把轮数降低一半。  
  最后，在计算安全场景下，通过引入 **PRG**，进一步将每个门的元素通信量降低到 **2** 和 **2.5**。  
  因此，这篇工作的贡献主要体现在：在保持 DN 框架的同时，同时优化了**通信量**与**轮复杂度**。

- **《Scalable Multiparty Computation from Non-linear Secret Sharing》**, CRYPTO 2024  
  该工作研究诚实大多数、半诚实场景下的无条件安全 MPC，并可容忍 $t < (1/2 - \delta) \cdot n $,总复杂度达到$ O(|C| \log |F|).  
  其核心技术不再是传统的线性打包秘密分享，而是采用了一种**非线性的秘密分享方案**。

- **《Honest Majority MPC with $\tilde O(|C|)$ Communication in Minicrypt》**, EUROCRYPT 2025  
  该工作在诚实大多数场景下，利用 **Minicrypt** 假设实现高效 MPC。  
  每个门的复杂度为 $O(\ell + \kappa),$
  其中 $\ell$ 为域元素比特长度，$\kappa$ 为安全参数。  
  相比 2021 年基于 Hall’s Marriage Theorem 的工作，这篇论文不再强求完美安全，而是实现了统计安全；同时也不再要求很大的域。  
  其技术核心是使用 **packed Beaver triples** 批量处理多个门，并通过 **OLE** 在 Minicrypt 技术下实现这些相关性。  
