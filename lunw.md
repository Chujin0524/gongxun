**Dynamic Adaptive APF Framework**  
├── **Planning Layer**  
│    ├── Parameters: \( K_m(t), K_{ap}(t), W_{th}(t) \)  
│    └── State Input: \( s(t) \)  
├── **TD3 Algorithm Core**  
│    ├── Actor Network: 高斯采样生成动作 \( a_t \)  
│    ├── Critic Network: 评估动作价值 \( Q(s_t, a_t) \)  
│    └── Experience Replay: 存储交互数据 \( (S_i, A_i, R_i, S_{i+1}) \)  
└── **Reward & Transition**  
     ├── Reward Mechanism: \( R_{\text{mod}}, R_{\text{side}}, R_{\text{smooth}} \)  
     └── State Transition: \( S \rightarrow A \rightarrow R \rightarrow D \rightarrow S' \)  

**TD3 Network**  
├── **Actor**  
│    └── 输入: \( s_t \) → 输出: \( a_t \)（含高斯噪声）  
├── **Critic 1 & 2**  
│    └── 输入: \( s_t, a_t \) → 输出: \( Q_1(s_t, a_t), Q_2(s_t, a_t) \)  
└── **Target Networks**  
     └── 软更新频率: \( \tau = 0.005 \)  