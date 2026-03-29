```mermaid
帮我作出这部分预览：
graph LR
    %% 全局样式设置
    classDef yellowBox fill:#FFF4DD,stroke:#D4A017,stroke-width:2px;
    classDef blueBox fill:#E1F5FE,stroke:#01579B,stroke-width:1px;

    %% 1. 实验分组阶段
    subgraph Grouping ["实验分组"]
        A1["对照组 (HEMn-LP)"]
        A2["实验组 (A375)"]
    end
    class Grouping yellowBox;
    class A1,A2 blueBox;

    %% 2. 细胞功能表型检测阶段
    subgraph Detection ["细胞功能表型检测 (湿实验验证)"]
        B1["形态学采集与AI特征提取<br/>(速度/密度/不规则度/清晰度)"]
        B2["增殖能力检测<br/>(MTS法)"]
        B3["水平迁移能力检测<br/>(划痕实验)"]
        B4["跨基质侵袭能力检测<br/>(Transwell实验)"]
    end
    class Detection yellowBox;
    class B1,B2,B3,B4 blueBox;

    %% 3. 数据分析与关联阶段
    subgraph Analysis ["特征关联与统计分析"]
        C1["Pearson相关性分析<br/>(边界特征 vs 迁移/侵袭能力)"]
        C2["SPSS 26.0 统计检验<br/>(P < 0.05)"]
    end
    class Analysis yellowBox;
    class C1,C2 blueBox;

    %% 4. 分子机制验证阶段
    subgraph Mechanism ["分子机制研究"]
        D1["转录组测序与分析"]
        D2["免疫荧光染色<br/>(细胞骨架/伪足)"]
        D3["Western Blot检测<br/>(EMT相关蛋白: E-cad/N-cad/Vim)"]
    end
    class Mechanism yellowBox;
    class D1,D2,D3 blueBox;

    %% 5. AI闭环优化阶段
    subgraph AICycle ["AI模型优化 (干实验反馈)"]
        E1["机制结果反馈至AI模型"]
        E2["优化特征提取权重<br/>(解决'黑箱问题')"]
    end
    class AICycle yellowBox;
    class E1,E2 blueBox;

    %% 连接关系
    A1 & A2 --> B1 & B2 & B3 & B4
    B1 & B2 & B3 & B4 --> C1
    C1 --> C2
    C2 --> D1
    D1 --> D2 & D3
    D2 & D3 --> E1
    E1 --> E2

    %% 闭环回流箭头
    E2 -.->|"干湿结合, 以干促湿, 以湿调干"| B1
