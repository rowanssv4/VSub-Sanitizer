# Network Space Proxy Fingerprint Intelligence Collector (NSPFIC)

[📄 English Description](#english-version) | [📄 中文说明](#中文版本)

---

## English Version

### 🚨 Crucial Statement: DO NOT Abuse Resources
* **Strict Compliance**: This repository runs under strict adherence to GitHub Terms of Service (TOS). 
* **Resource Constraint**: The automated lifecycle executes in less than 20-25 seconds per run, utilizing a circuit-breaker mechanism to limit third-party API queries to under 120 requests. This ensures zero strain on GitHub Actions infrastructure or third-party network bandwidth.
* **Legal Disclaimer**: This project is strictly for academic research, protocol analysis, and DevOps training. The developer assumes no liability for any network penetration behaviors, data misuse, or system risks caused by users interacting with the output datasets (`nodes.txt` / `sub.txt`).

---

### 1. What It Does
This project is an automated pipeline that aggregates scattered, public proxy fingerprint data from the open internet, sanitizes illegal traffic signatures, validates core autonomous system numbers (ASN), and persists structured明文/密文 (plaintext/ciphertext) routing records.

### 2. The Purpose (Why This Tool)
The internet is flooded with non-structured, ephemeral public routing assets. The purpose of this collector is to harvest these distributed datasets and transform chaotic open-source threat intelligence into highly organized, tag-enhanced network telemetry metrics for experimental simulation.

### 3. Technical Decisions (Why We Do It This Way)
* **The No-Ping Policy**: Traditional connection testing (PING/TCP speed tests) during automated execution heavily degrades network throughput, chokes I/O queues due to massive dead-node timeouts, and triggers provider-level anti-DDoS locks. By eliminating local active probing and implementing an external ASN reverse-lookup mechanism instead, the script executes instantly without freezing.
* **Dual-Engine Fingerprinting**: We utilize an online API penetration engine for the top 120 seed paths to extract real-time carrier traits (`+Residential`, `+Datacenter`), combined with an offline 4-character regex lexical matrix for the remaining bulk nodes. This approach avoids API rate-limiting (429 Too Many Requests) while achieving precise categorization.
* **AST Pre-filtering**: It inspects incoming payloads to strip away malicious HTML redirects or structural anomalies, keeping the payload pool completely standardized.

### 4. Infrastructure Selection (Why GitHub)
* **Decentralized Execution Edge**: GitHub Actions provides a pristine, high-availability runtime environment with global network routing edges, ensuring optimal throughput when polling distributed intelligence repositories.
* **Version-Controlled Intelligence**: Leveraging Git's tree state allows for frictionless persistence. By utilizing standard version tracking, the collector synchronizes state delta records cleanly via headless bot pushes.

---

## 中文版本

### 🚨 严正声明：请勿滥用本项目资源
* **合规约束**：本项目严格遵循 GitHub 服务条款（TOS）运行。
* **算力熔断**：自动化流水线的单次生存期严格控制在 20-25 秒以内，并引入了高频请求熔断机制，将第三方在线查询限制在 120 次以内，绝不滥用 GitHub Actions 算力及外部网络带宽。
* **免责申明**：本项目仅供学术研究、协议分析及运维技术练习使用。使用者因不当操作或违规使用派生数据集（`nodes.txt` / `sub.txt`）所引发的任何形式的系统风险或法律责任，均由使用者本人承担。

---

### 1. 它做什么 (What It Does)
本项目是一个自动化流水线工具，用于高频聚合互联网中公开且散落的网络代理空间指纹信息，并对流量特征进行合规解包与反混淆，同时交叉验证真实的全球 BGP 自治系统（ASN）归属，最终持久化输出结构化的明文与密文路由数据集。

### 2. 做的目的 (Why This Tool)
公网中的分布式代理资产往往是非结构化、极易失效且充斥着虚假备注的。开发该收集器的目的，是为了将这些无序的、混杂的开源威胁情报，通过技术手段提炼并转化为具备高价值拓扑标签、格式统一的网络测绘指标，用于分布式容灾实验。

### 3. 为什么这么做 (Why We Do It This Way)
* **全面拔除本地测速**：传统的 TCP 连接性测速和 PING 在 Actions 虚拟机环境下运行极易由于海量死节点的超时（Timeout）堆积导致 I/O 队列严重卡死，甚至会被运营商误判为异常流量发起限制。采用“全量放出不设卡、移交客户端测速”的策略，能确保脚本以极高吞吐瞬间完成运行。
* **双擎混合指纹清洗**：为了对抗第三方权威数据库的请求频率限制（429 Too Many Requests），系统采取分流设计：前 120 个种子节点通过在线 API 穿透反查、挖掘真实的 `+住宅IP` 或 `+商业机房` 骨干特质；其余大部队则无缝切入本地轻量级 4 字正则词典秒级认领国别，在防止被封 IP 的同时实现了全量精准分类。
* **结构化反重定向**：在解析载荷前进行语法树指纹粗筛，拦截并剔除所有携带恶意网页源码或异常伪装的节点，确保持久化明文池的极纯净度。

### 4. 为什么选择 GitHub (Why GitHub)
* **全球化高可用边缘算力**：GitHub Actions 提供了干净、具备全球顶级多路由传输的运行时环境，能够保证在并发拉取全球不同国家和地区的分布式网络资源时的吞吐率。
* **天然的版本控制情报库**：利用 Git 的版本演进特性，可以在无需配置独立昂贵数据库的前提下，通过 Headless 机器人的强推操作（Force Push），无缝实现全局数据的增量覆盖、跟踪以及历史报告持久化。
