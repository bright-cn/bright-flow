## 量子计算对密码学的影响

### 要点

-   由于 Shor 算法的存在，量子计算机对 RSA 和 ECC 等经典密码算法构成威胁。
-   AES 容易受到 Grover 算法攻击，但影响程度低于 RSA 和 ECC。AES-256 比 AES-128 更具抵抗力。
-   后量子密码学（PQC）旨在开发能够抵抗量子计算机攻击的算法。
-   量子密钥分发（QKD）基于量子力学提供安全的密钥交换，但面临实际应用挑战。
-   NIST 正在标准化 PQC 算法，各组织也在探索 QKD/PQC 混合解决方案。
-   发生重大量子攻击的时间尚不确定，但有必要主动采取措施。

---

### 概述

量子计算对现代密码学构成重大威胁。Shor 和 Grover 等量子算法可以破解或削弱广泛使用的加密方法，因此有必要开发并采用抗量子密码解决方案。本报告概述量子计算对现有密码算法的影响，并探讨后量子密码学（PQC）和量子密钥分发（QKD）等潜在解决方案。

---

### 详细分析

#### 经典密码学的漏洞

经典密码算法依赖经典计算机难以解决的数学问题，但这些问题容易受到量子算法攻击。

| 算法 | 漏洞 | 量子算法 | 影响                                                              |
| :-------- | :------------ | :---------------- | :------------------------------------------------------------------ |
| RSA       | 因数分解     | Shor 算法  | 高效分解大整数，破解 RSA 加密   |
| ECC       | 离散对数  | Shor 算法  | 高效解决离散对数问题，破解 ECC 加密 |
| AES       | 暴力破解   | Grover 算法| 缩小搜索空间，削弱 AES 安全性；AES-256 更强 |

如果开发出足够强大的量子计算机，Shor 算法可以高效分解大整数，使 RSA 和 ECC 失去作用 [http://greekcrisis.net/shors-algorithm-quantum-computers/]。破解 RSA-2048 大约需要 4,000 个量子比特，破解 ECC-256 则大约需要 2,500 个量子比特 [https://ej-compute.org/index.php/compute/article/view/146]。

Grover 算法会缩小 AES 的暴力搜索空间，从而削弱其安全性 [https://ej-compute.org/index.php/compute/article/view/146]。与 AES-128 或 AES-192 相比，AES-256 更能抵御量子攻击 [https://crypto.stackexchange.com/questions/6712/is-aes-256-a-post-quantum-secure-cipher-or-not]。

#### 量子计算资源

破解 RSA-2048 需要约 4,000 个量子比特和数百万次门操作，未来十年内可能实现 [https://ej-compute.org/index.php/compute/article/view/146]。到 2030 年，可能可以花费约 10 亿美元构建一台能在数小时内破解 RSA-2048 的量子计算机 [https://crypto.stackexchange.com/questions/102671/is-aes-128-quantum-safe]。IBM 拥有 1,121 量子比特的“Condor”处理器，领先平台的目标是将双量子比特门保真度提高到 99.9% 至 99.99% [https://methodologists.net/Exploring-the-Transformative-Advancements-in-Quantum-Computing-and-Their-Global-Impact-in-2024]。

#### 后量子密码学（PQC）

后量子密码学（PQC）旨在开发能够抵御经典计算机和量子计算机攻击的密码算法 [https://en.wikipedia.org/wiki/Post-quantum_cryptography]。

**PQC 算法类型**

| 算法类型       | 示例                                  | 特征                                                              |
| :------------------- | :---------------------------------------- | :--------------------------------------------------------------------------- |
| 基于格        | CRYSTALS-Kyber、CRYSTALS-Dilithium、NTRU | 基于格问题的困难性                                    |
| 多变量         | Rainbow                                   | 基于求解多变量多项式方程组的困难性 |
| 基于哈希           | SPHINCS+                                  | 基于密码哈希函数的安全性                         |
| 基于编码           | Classic McEliece                          | 基于一般线性码解码的困难性                       |
| 基于同源        | CSIDH                                     | 基于超奇异椭圆曲线之间的同源                        |
| 对称密钥抗量子性 | AES 和 SNOW 3G                     | 抵御已知对称密钥量子攻击的后量子能力 |

与前量子算法相比，PQC 算法通常需要更大的密钥 [https://en.wikipedia.org/wiki/Post-quantum_cryptography]。

**NIST 标准化**

NIST 正在开展后量子密码学标准化流程，以选择 PQC 算法 [https://en.wikipedia.org/wiki/Post-quantum_cryptography]。NIST 已发布前三项最终确定的后量子加密标准：CRYSTALS-Kyber（ML-KEM）、CRYSTALS-Dilithium（ML-DSA）和 SPHINCS+ [https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards]。

#### 量子密钥分发（QKD）

QKD 利用量子力学原理提供安全的密钥交换方法 [https://www.iosrjournals.org/iosr-jce/papers/Vol16-issue2/Version-11/A0162110109.pdf]。由于窃听会干扰量子系统，因此会产生可检测的异常 [https://en.wikipedia.org/wiki/Quantum_key_distribution]。

**QKD 协议**

| 协议 | 描述 |
| :------- | :---------- |
| BB84     | 首个 QKD 协议 |
| E91      | 使用纠缠光子 |
| COW      | 相干单向协议 |

实际挑战包括秘密密钥速率、距离、尺寸、成本和实际安全性 [https://arxiv.org/abs/1606.05853]。美国国家安全局认为，在保护国家安全系统中的数据方面，抗量子密码学（PQC）比 QKD 更具成本效益，也更易于维护 [https://www.nsa.gov/Cybersecurity/Quantum-Key-Distribution-QKD-and-Quantum-Cryptography-QC/]。

#### 混合方法

人们正在探索集成 PQC 和 QKD 的混合安全系统 [https://www.gsma.com/newsroom/wp-content/uploads//IG.18-Hybrid-QKD-and-PQC-security-scenarios-and-use-cases-Whitepaper-v1.0-002.pdf]。预计 2025 年至 2030 年间，网络运营商将在 QKD 开发和实施方面投入超过 60 亿美元 [https://smartinfrastructuremagazine.com/news/quantum-key-distribution-network-operators-to-spend-6-3-billion-over-next-six-years]。

#### 风险评估与时间表

量子计算不断进步，因此迫切需要向量子安全替代方案迁移 [https://ej-compute.org/index.php/compute/article/view/146]。密码漏洞可能在未来 5 至 10 年内显现 [https://ej-compute.org/index.php/compute/article/view/146]。

---

### 主要引用

- [Shor 算法的实现及其量子演示……：JSR](https://www.jsr.org/hs/index.php/path/article/view/6348)

- [用于破解 RSA 的 Shor 算法实现与分析……](https://www.researchgate.net/publication/377245624_Implementation_and_Analysis_of_Shor's_Algorithm_to_Break_RSA_Cryptosystem_Security)

- [量子 AI：Shor 算法，量子计算机如何破解密码学……](http://greekcrisis.net/shors-algorithm-quantum-computers/)

- [RSA/ECC 面对量子计算的漏洞：r/cryptography，Reddit](https://www.reddit.com/r/cryptography/comments/1ajubq8/vulnerability_of_rsaecc_to_qc/)

- [量子计算对网络安全的影响：Shor 算法……](https://www.academia.edu/127333737/Cyber_Security_Implications_of_Quantum_Computing_Shors_Algorithm_and_Beyond)

- [量子计算对密码系统的影响：……的紧迫性](https://ej-compute.org/index.php/compute/article/view/146)

- [通过量子计算探索 AES 加密实现……](https://sciencepublishinggroup.com/article/10.11648/j.ajcst.20240704.12)

- [CSRC 演示文稿 | CSRC：NIST 计算机安全资源中心](https://csrc.nist.gov/Presentations/2024/practical-cost-of-grover-for-aes-key-recovery)

- [AES-256 是否是一种后量子安全密码？](https://crypto.stackexchange.com/questions/6712/is-aes-256-a-post-quantum-secure-cipher-or-not)

- [RSA 因量子攻击而消亡并非遥不可及……：Ars Technica](https://arstechnica.com/information-technology/2023/01/fear-not-rsa-encryption-wont-fall-to-quantum-computing-anytime-soon/)

- [中国研究人员使用量子计算机破解 RSA 加密](https://www.csoonline.com/article/3562701/chinese-researchers-break-rsa-encryption-with-a-quantum-computer.html)

- [量子计算与 RSA 算法面临的风险](https://robharrisoneu.substack.com/p/quantum-computing-and-the-risks-to)

- [量子计算突破可能破解 ECC 密码学……](https://quantumzeitgeist.com/quantum-computing-breakthrough-could-crack-ecc-cryptography-exposing-internet-secrets-claims-psiquantum-researcher/)

- [量子计算与普通计算破解 ECC 所需时间对比](https://crypto.stackexchange.com/questions/35384/quantum-vs-regular-computing-time-to-break-ecc)

- [AES-128 是否具备量子安全性？：Cryptography Stack Exchange](https://crypto.stackexchange.com/questions/102671/is-aes-128-quantum-safe)

- [AES-128 还能维持安全多少年？：r/cryptography，Reddit](https://www.reddit.com/r/cryptography/13lp9nf/how_many_decades_aes128_will_last/)

- [AES-256 加入抗量子行列：Fierce Electronics](https://www.fierceelectronics.com/electronics/aes-256-joins-quantum-resistance)

- [2024 年量子计算现状：创新、挑战与……](https://methodologists.net/Exploring-the-Transformative-Advancements-in-Quantum-Computing-and-Their-Global-Impact-in-2024)

- [量子计算的当前状况：IEEE Computer Society](https://www.computer.org/publications/tech-news/research/current-state-of-quantum-computing)

- [量子硬件格局：相互竞争的架构](https://quantumzeitgeist.com/quantum-hardware/)

- [量子计算的实际影响：美国国家……研究所](https://www.nist.gov/document/post-quantum-cryptography-and-cybersecurity)

- [2024 年量子威胁时间表报告：Global Risk Institute](https://globalriskinstitute.org/publication/2024-quantum-threat-timeline-report/)

- [区块链面临的量子威胁：摘要与时间表分析](https://link.springer.com/article/10.1007/s42484-023-00105-4)

- [后量子密码学：维基百科](https://en.wikipedia.org/wiki/Post-quantum_cryptography)

- [首批四种抗量子密码算法：Embedded](https://www.embedded.com/first-four-quantum-resistant-cryptographic-algorithms/)

- [微软的抗量子密码技术现已推出](https://techcommunity.microsoft.com/blog/microsoft-security-blog/microsofts-quantum-resistant-cryptography-is-here/4238780)

- [探索椭圆曲线密码学与基于格的密码学，面向未来……](https://medium.com/@RocketMeUpCybersecurity/exploring-elliptic-curve-vs-lattice-based-cryptography-for-future-security-0c8426c97deb)

- [[PDF] 基于格的……性能比较与迁移分析](https://eprint.iacr.org/2020/990.pdf)

- [[PDF] 基于编码的密码学综述：arXiv](https://arxiv.org/pdf/2201.07119)

- [了解基于格的密码学：Blue Goat Cyber](https://bluegoatcyber.com/blog/understanding-lattice-based-cryptography/)

- [基于编码的密码学综述：克莱姆森大学](https://open.clemson.edu/cgi/viewcontent.cgi?article=5227&context=all_theses)

- [NIST 发布首批 3 项最终确定的后量子加密标准](https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards)

- [必须采用后量子密码学来保护你的系统 | Gartner](https://www.gartner.com/en/articles/post-quantum-cryptography)

- [后量子密码世界中的安全数据基础设施](https://futurumgroup.com/research-reports/secure-data-infrastructure-in-a-post-quantum-cryptographic-world/)

- [NCSC 将后量子密码迁移截止日期定为 2035 年](https://www.infosecurity-magazine.com/news/ncsc-post-quantum-cryptography/)

- [PQC（后量子密码学）：新的网络安全威胁](https://hackhunting.com/2025/01/11/post-quantum-cryptography-the-new-network-security-threat/)

- [探索后量子密码学：综述与未来方向……](https://www.mdpi.com/2227-7080/12/12/241)

- [[PDF] 基于哈希的……中部分哈希函数的性能比较](https://jomardpublishing.com/UploadFiles/Files/journals/JTME/V5N3/KaratayM_et_al.pdf)

- [[PDF] 不同密码哈希函数的比较分析](http://www.diva-portal.org/smash/get/diva2:1885074/FULLTEXT01.pdf)

- [多变量密码学：SpringerLink](https://link.springer.com/referenceworkentry/10.1007/978-3-642-27739-9_421-2)

- [量子密钥分发协议：综述](https://www.iosrjournals.org/iosr-jce/papers/Vol16-issue2/Version-11/A0162110109.pdf)

- [量子密钥分发：维基百科](https://en.wikipedia.org/wiki/Quantum_key_distribution)

- [量子密钥分发面临的实际挑战：arXiv.org](https://arxiv.org/abs/1606.05853)

- [量子密钥分发（QKD）和量子密码学 QC](https://www.nsa.gov/Cybersecurity/Quantum-Key-Distribution-QKD-and-Quantum-Cryptography-QC/)

- [混合 QKD 与 PQC 安全场景和用例白皮书](https://www.gsma.com/newsroom/wp-content/uploads//IG.18-Hybrid-QKD-and-PQC-security-scenarios-and-use-cases-Whitepaper-v1.0-002.pdf)

- [量子密钥分发：网络…… | Smart Infrastructure Magazine](https://smartinfrastructuremagazine.com/news/quantum-key-distribution-network-operators-to-spend-6-3-billion-over-next-six-years)