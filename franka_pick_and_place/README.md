# Franka Pick-and-Place with RL

Training a Franka Emika Panda robot to pick colored boxes and place them in matching colored buckets using reinforcement learning (PPO).

![](./model/panda.png)


## Project Structure

```
mujoco_projects/
└── franka_pick_and_place/
    ├── pick_and_place_train.ipynb       # Main training notebook
    ├── pick_and_place_train.py          # Python script version
    ├── franka_pick_place_ppo.zip        # Trained PPO model
    └── README.md                         # This file
```

## Requirements

- MuJoCo 3.4.0
- Gymnasium 0.29.0
- Stable Baselines3 2.2.0
- PyTorch 2.10.0+ (with CUDA for GPU acceleration)

## Setup

1. Install dependencies in the MuJoCo environment:
   ```bash
   cd /home/cvincen6/mujoco-3.4.0
   source .venv/bin/activate  # or source venv/bin/activate
   ```

2. Open the notebook:
   ```bash
   jupyter notebook pick_and_place_train.ipynb
   ```

## Training

The notebook trains a Franka Panda robot for 300,000 timesteps using PPO with:
- **Action Space**: 8D (7 arm joints + 1 gripper)
- **Observation Space**: 51D (arm state + box positions)
- **Task**: Pick 12 colored boxes and sort them into 4 matching colored buckets

## Model

The trained model is saved as `franka_pick_place_ppo.zip` and can be loaded with:
```python
from stable_baselines3 import PPO
model = PPO.load("franka_pick_place_ppo")
```

## Notes

- The notebook references the Franka model from `mujoco-3.4.0/model/franka_panda/`
- Scene file with boxes and buckets: `franka_panda/pick_place_scene.xml`
- Update import paths in the notebook if moving this directory
