---

# DQN-AirRaid-Gym

This repository contains a project that implements a Deep Q-Network (DQN) model to play the Atari 2600 game Air Raid using the Gymnasium framework. The model is trained using reinforcement learning techniques to achieve high scores by learning optimal strategies for the game.

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Training the Model](#training-the-model)
- [Evaluating the Model](#evaluating-the-model)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Introduction

Air Raid is a classic Atari 2600 game where players must defend their city from an aerial assault. This project leverages the power of Deep Q-Networks (DQN), a type of reinforcement learning, to create an AI agent capable of playing and mastering the game.

## Installation

To get started, clone the repository and install the necessary dependencies:

```bash
git clone https://github.com/yourusername/DQN-AirRaid-Gym.git
cd DQN-AirRaid-Gym
pip install -r requirements.txt
```

Ensure you have the Gymnasium framework and Stable Baselines3 library installed, along with other dependencies listed in the `requirements.txt` file.

## Usage

### Running the Notebook

To run the entire project, including training and evaluating the model, open the provided Jupyter notebook `AirRaid_DNQ.ipynb` and execute the cells in sequence. The notebook contains all the necessary code for:

1. Setting up the environment and dependencies.
2. Defining and training the DQN model.
3. Saving the trained model.
4. Loading the trained model for evaluation.
5. Rendering the gameplay of the trained model.

### Training the Model

Within the notebook, the following code initializes and trains the DQN model:

```python
# Define the DQN model
model = DQN('CnnPolicy', env, verbose=1, tensorboard_log="./logs/")

# Train the model
model.learn(total_timesteps=1000000, progress_bar=True)

# Save the trained model
model.save("first_1mil")
```

### Evaluating the Model

To load and evaluate the trained model, use the following code in the notebook:

```python
# Load the trained model
model = DQN.load("./logs/first_1mil.zip")

# Evaluate the model
obs = env.reset()
while True:
    action, _states = model.predict(obs, deterministic=True)
    obs, reward, terminated, info = env.step(action)
    if terminated:
        obs = env.reset()
        break
    env.render()
```

### Watching the Trained Model

The evaluation code snippet above will also render the gameplay of the trained model.

## Results

Training progress and results, including graphs of rewards and losses, will be saved in the `logs` directory. The final trained model will be saved as `first_1mil.zip`.

## Contributing

Contributions are welcome! If you have any ideas, suggestions, or improvements, please feel free to open an issue or submit a pull request. Follow these steps to contribute:

1. Fork the repository
2. Create a new branch (`git checkout -b feature-branch`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature-branch`)
5. Open a pull request

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---
