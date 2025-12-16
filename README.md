# MPC-Classics
 A Paper Collection for Beginners

## 综述推荐
[2022 SANDS -Concretely efficient secure multi-party computation.pdf](https://github.com/kafei-cy/MPC-Classics/blob/main/%E2%AD%902022%20SANDS%20-Concretely%20efficient%20secure%20multi-party%20computation.pdf)： 冯登国老师和杨糠老师写的综述，内涵大量经典论文引用，适合刚进入mpc小组的同学学习，尽早确定研究方向。

## 各方向论文推荐

### FuzzyPsi 论文推荐 (from kafei-cy)
主要研究Lp距离和汉明距离相关的FuzzyPsi文章,这里分两种不同架构来列举，再细分为不同假设下的文章
目录结构：
```
from kafei-cy
└── FuzzyPSI
    └── L_P distance(also L_infty)
        ├── based_on_FuzzyMatching
        │   ├── apart假设
        │   └── seperate假设
        └── structure-aware PSI
```

### PSO 论文推荐（from Azzzting）
论文主要是做PSO方面的工作，包含PSI，PSU，PSI-CARD等，同时也包含两方和多方场景。在阅读论文之前建议了解下述组件的功能，构造可以在之后了解。
主要的组件：
- OPRF/OPPRF
- VOLE
- OKVS
- OT

组里自己提出的组件：
- MCRG
- J-PEQT
