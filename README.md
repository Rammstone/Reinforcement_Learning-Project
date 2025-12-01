# Warehouse Navigation using PPO
## Reinforcement Learning Project

---

## 📝 Abstract
This project implements a Reinforcement Learning (RL) agent that navigates a 2D warehouse grid environment containing both static and dynamic obstacles. A custom `WarehouseEnv` simulates shelves, robots, and a goal location. The agent is trained using **Proximal Policy Optimization (PPO)** from Stable Baselines3.

The project covers environment design, reward shaping, PPO architecture, training checkpoints, and evaluation results.

---

## 📌 Features
- Custom Gym-compatible warehouse environment  
- Dynamic + static obstacles  
- PPO-based training  
- Training checkpoints  
- Visual results and navigation behavior  
- Fully simulated (no external dataset)

---

## 🚀 Problem Statement
The RL agent must:
- Reach the goal  
- Avoid static shelves  
- Avoid dynamic robots  
- Learn a safe and efficient navigation policy  

The observation space includes:
- Robot position  
- Goal position  
- Warehouse obstacle map  

---

## 🧠 RL Training Process
Training uses **Stable Baselines3 PPO**, interacting with the custom environment.

### 🎯 PPO Objective
```
L_CLIP(θ) = E[min(r_t(θ) Â_t, clip(r_t(θ), 1−ε, 1+ε) Â_t)]
```
Where:
- `r_t(θ)` = probability ratio  
- `Â_t` = GAE advantage  
- `ε` = clipping parameter  

This stabilizes training by preventing overly large updates.

---

## 🎮 Reward Structure
| Event | Reward |
|-------|--------|
| Collision | Large negative |
| Step taken | Small negative |
| Goal reached | Large positive |

### GAE Advantage Calculation
```
δ_t = r_t + γV(s_(t+1)) – V(s_t)
Â_t = Σ (γλ)^l δ_(t+l)
```

---

## 🏋️ Training Steps
1. Agent interacts with environment → collects (state, action, reward, next state)  
2. Compute GAE advantages  
3. Update actor & critic networks  
4. Save model checkpoints every *50,000* timesteps  
5. Continue until convergence  

---

## 📂 Training Checkpoints
- **Initial model** – random behavior  
- **50k, 100k, 150k** – improvements in reward and collision reduction  
- **Final model** – robust navigation with efficient pathing  

---

## ✅ Outcome
The PPO agent:
- Reaches the goal consistently  
- Avoids shelves and moving robots  
- Learns short, efficient paths  
- Shows stability and convergence  

---

## 📷 Results
The following outputs were generated during evaluation:
- Initial grid layout  
- Movement across grid  
- Dynamic obstacle avoidance  
- Final goal reach  

(Place images or GIFs here if available)

---

## 📦 Project Structure
```
📁 warehouse-rl-ppo
 ├── warehouse_env.py
 ├── train.py
 ├── evaluate.py
 ├── checkpoints/
 ├── README.md
```

---

## 🏁 Conclusion
This project demonstrates the application of **Proximal Policy Optimization** for warehouse navigation.  
It forms a strong base for:
- Multi-agent navigation  
- Real robot deployment  
- More advanced warehouse automation systems  

---

## 👥 Authors
- Samridh Ramesha  
- Ansh Goyal  
- Chandan Singh  
- Bhanodhay Rao  

---

