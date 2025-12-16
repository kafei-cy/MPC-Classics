# [RS21]VOLE-PSI: Fast OPRF and Circuit-PSI from Vector-OLE
- EUROCRYPT 2021
- 前置知识：了解OPRF OPPRF VOLE OKVS这些组件的基本概念，理解PSI是在做什么，对安全模拟有大概的理解
- 本文提出了如何从VOLE构造OPRF进一步构造PSI协议，如何使用Random Oracle抵御恶意敌手，是后面VOLE做PSI工作的基础。
- 关键贡献：首次将VOLE与PaXoS构建的OKVS结合，构造出通信和计算复杂度均为O(n)的OPRF。使用Random Oracle降低恶意安全模型下的通信开销，将抵抗恶意敌手的PSI需OPRF输出2\kappa降低为\kappa.
