# Add cart pendulum

## What is cart pendulum?
It's basically same as 'CartPole', but
- env for swing -> inverted pendulum control
- env does not finish even when Pole angle exceed 0.418 rad (24°)
- initial pole angle can be over 0.418
- input is continuas value within [-1.0, 1.0]. (1.0 means pushing car to right with maximum power, and -1.0 is left. if 0, do nothing.)

## Usage
The Gymnasium API models environments as simple Python `env` classes. Creating environment instances and interacting with them is very simple- here's an example using the "CartPole-v1" environment:

```python
import gymnasium as gym
import random
env = gym.make("CartPendulum-v0")

observation, info = env.reset(seed=42)
for _ in range(1000):
    action = random.random() * 2 - 1.0 #[-1.0, 1.0]
    observation, reward, terminated, truncated, info = env.step(action)

    if terminated or truncated:
        observation, info = env.reset()
env.close()
```
