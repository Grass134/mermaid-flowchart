# 我的流程图

```mermaid
graph TD
    %% 全局样式定义
    classDef core fill:#E8EAF6,stroke:#3F51B5,stroke-width:3px,color:#1A237E,font-weight:bold;
    classDef experiment fill:#FFFFFF,stroke:#03A9F4,stroke-width:1px;
    classDef category fill:#FFF9C4,stroke:#FBC02D,stroke-width:2px,font-weight:bold;

    %% ==================== 中央核心逻辑轴 ====================
    subgraph CoreAxis ["核心逻辑轴"]
        direction TB
        Center1((("AI 皮肤镜图像<br/>特征提取")))
        Center2((("细胞形态边界<br/>不规则表型")))
        Center3((("分子机制解析<br/>(EMT通路)")))
        Center4((("AI 模型权重<br/>闭环优化")))
        
        Center1 --- Center2
        Center2 --- Center3
        Center3 --- Center4
    end
    class CoreAxis category;
    class Center1,Center2,Center3,Center4 core;

    %% ==================== 左侧：湿实验验证 ====================
    subgraph WetExp ["湿实验验证 (细胞表型)"]
        direction TB
        W1["MTS法 (增殖能力)"]
        W2["划痕实验 (迁移能力)"]
        W3["Transwell (侵袭能力)"]
    end
    class WetExp category;
    class W1,W2,W3 experiment;

    %% ==================== 右侧：干实验分析 ====================
    subgraph DryExp ["干实验分析 (特征关联)"]
        direction TB
        D1["Pearson 相关性分析"]
        D2["SPSS 26.0 统计检验"]
        D3["边界特征 vs 恶性度"]
    end
    class DryExp category;
    class D1,D2,D3 experiment;

    %% ==================== 底部：深度机制研究 ====================
    subgraph BioMech ["深度机制研究"]
        direction LR
        M1["转录组测序 (RNA-seq)"]
        M2["免疫荧光 (细胞骨架)"]
        M3["Western Blot (EMT蛋白)"]
        
        M1 --- M2
        M2 --- M3
    end
    class BioMech category;
    class M1,M2,M3 experiment;

    %% ==================== 逻辑连接 ====================
    B1["A375 vs HEMn-LP"]
    class B1 experiment;

    Center1 -.->|"形态学匹配"| B1
    B1 --> WetExp
    WetExp --> Center2
    
    Center2 --> DryExp
    DryExp --> Center3
    
    Center3 --> BioMech
    BioMech --> Center4

    %% ==================== 闭环反馈 ====================
    Center4 ==>|"以湿调干: 消除黑箱"| Center1
