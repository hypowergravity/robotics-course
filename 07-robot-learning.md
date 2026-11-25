# Stage 7: Robots That Learn

**Start here:** [Karpathy's reinforcement learning demo](https://cs.stanford.edu/people/karpathy/convnetjs/demo/rldemo.html)

Instead of writing every behaviour by hand, you can reward a robot for good outcomes and let it discover the behaviour. Learn the core ideas on small problems first, then move to simulated robots, and finally to the large policies that are now trained from human demonstrations.

## Foundations

### [karpathy/convnetjs](https://github.com/karpathy/convnetjs)
The library behind the demo you opened. It is small enough to read in an afternoon.

### [karpathy/micrograd](https://github.com/karpathy/micrograd)
A tiny automatic differentiation engine that shows how neural network training works underneath.

### [karpathy/nn-zero-to-hero](https://github.com/karpathy/nn-zero-to-hero)
Notebooks and lecture material that build neural networks from scratch. Good preparation if deep learning is new to you.

### [dennybritz/reinforcement-learning](https://github.com/dennybritz/reinforcement-learning)
Code and exercises for reinforcement learning algorithms, following the standard textbook.

### [ShangtongZhang/reinforcement-learning-an-introduction](https://github.com/ShangtongZhang/reinforcement-learning-an-introduction)
Python code reproducing the examples and figures in Sutton and Barto's textbook.

### [openai/spinningup](https://github.com/openai/spinningup)
A teaching resource with explanations and clean implementations of the main deep RL algorithms.

## Libraries to train agents

### [Farama-Foundation/Gymnasium](https://github.com/Farama-Foundation/Gymnasium)
The standard interface for RL environments. Learning it lets you swap algorithms and tasks freely.

### [DLR-RM/stable-baselines3](https://github.com/DLR-RM/stable-baselines3)
Reliable, well-documented implementations of common RL algorithms. Start here to train something quickly.

### [vwxyzjn/cleanrl](https://github.com/vwxyzjn/cleanrl)
Single-file implementations of RL algorithms, easy to read and modify once you want to understand the details.

### [google-deepmind/dm_control](https://github.com/google-deepmind/dm_control)
A control suite and tools for physics-based RL on MuJoCo.

### [Unity-Technologies/ml-agents](https://github.com/Unity-Technologies/ml-agents)
A toolkit for training agents in Unity environments.

## Robot learning in simulation

### [isaac-sim/IsaacLab](https://github.com/isaac-sim/IsaacLab)
NVIDIA's framework for robot learning at scale on the GPU.

### [google-deepmind/mujoco_playground](https://github.com/google-deepmind/mujoco_playground)
GPU-accelerated environments for locomotion and manipulation with sim-to-real examples.

### [leggedrobotics/legged_gym](https://github.com/leggedrobotics/legged_gym)
The well-known codebase for training legged robots to walk in simulation.

### [leggedrobotics/rsl_rl](https://github.com/leggedrobotics/rsl_rl)
A compact RL library used with legged_gym and Isaac Lab.

### [google/brax](https://github.com/google/brax)
A fast differentiable physics engine in JAX that trains policies in minutes.

### [kscalelabs/ksim](https://github.com/kscalelabs/ksim)
A modular framework for training humanoid policies in simulation.

## Learning from demonstrations

### [real-stanford/diffusion_policy](https://github.com/real-stanford/diffusion_policy)
Policies that generate robot actions with diffusion models, a leading approach for manipulation.

### [tonyzhaozh/act](https://github.com/tonyzhaozh/act)
The Action Chunking Transformer, a simple and effective way to learn bimanual tasks from a small number of demonstrations.

### [octo-models/octo](https://github.com/octo-models/octo)
An open generalist robot policy trained on many robots.

### [openvla/openvla](https://github.com/openvla/openvla)
An open vision-language-action model that follows language instructions.

### [Physical-Intelligence/openpi](https://github.com/Physical-Intelligence/openpi)
Open models and code for general-purpose robot policies.

### [NVIDIA/Isaac-GR00T](https://github.com/NVIDIA/Isaac-GR00T)
A foundation model for humanoid robot skills.

## What to be able to do before moving on

You should be able to train an agent on a Gymnasium task, explain reward, policy and value in plain words, and notice reward hacking when your agent finds an unintended shortcut. A good project is a simulated arm or walker trained with stable-baselines3.

## Trending and most-starred additions (checked 25 Nov 2026)

Star counts below are approximate figures reported by public aggregator pages on 25 Nov 2026, so treat them as a rough guide to popularity, not exact numbers. Entries without a count had no figure in the pages I could reach. Links not marked as checked are from memory, so confirm they open.

### The biggest project
[huggingface/lerobot](https://github.com/huggingface/lerobot) is at about 28.7k stars, with version 0.7.0 released on 5 Nov 2026. Its paper was accepted at ICLR 2026. It remains the best single place to learn the whole learning stack.

### Popular training frameworks
[RLinf/RLinf](https://github.com/RLinf/RLinf) is reinforcement learning infrastructure for embodied and agentic AI, listed at several thousand stars. [Farama-Foundation/Gymnasium-Robotics](https://github.com/Farama-Foundation/Gymnasium-Robotics) is a collection of robotics environments at about 2k stars. [fan-ziqi/robot_lab](https://github.com/fan-ziqi/robot_lab) is an Isaac Lab extension library at about 2k stars, [unitreerobotics/unitree_rl_lab](https://github.com/unitreerobotics/unitree_rl_lab) holds Unitree training code at about 1.5k, and [fan-ziqi/rl_sar](https://github.com/fan-ziqi/rl_sar) covers simulation checks and real deployment at about 1.3k. [Holiday-Robot/FlashSAC](https://github.com/Holiday-Robot/FlashSAC) is a fast off-policy RL method for high-dimensional robot control. [facebookresearch/habitat-lab](https://github.com/facebookresearch/habitat-lab) covers embodied navigation.

### Humanoid learning
[roboterax/humanoid-gym](https://github.com/roboterax/humanoid-gym) (about 2.0k stars) focuses on zero-shot sim-to-real humanoid RL. [YanjieZe/GMR](https://github.com/YanjieZe/GMR) (about 2.1k) is general motion retargeting from ICRA 2026. [YanjieZe/awesome-humanoid-robot-learning](https://github.com/YanjieZe/awesome-humanoid-robot-learning) (about 2.2k) is a paper list. [rohanpsingh/LearningHumanoidWalking](https://github.com/rohanpsingh/LearningHumanoidWalking) (about 1.1k) is an approachable walking project.

### A useful shortlist
A widely shared list of ten repositories for building AI robots names LeRobot, ROS 2, Isaac Lab, OpenVLA, MuJoCo, PyBullet, RoboSuite, ManiSkill, Habitat Lab and Diffusion Policy. That is a good sanity check for what the community actually uses.
