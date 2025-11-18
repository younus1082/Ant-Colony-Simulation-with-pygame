# 🐜 Ant Colony Simulation

A Python-based biological simulation using **Pygame**. This project simulates the natural foraging behavior of ants, demonstrating how complex group behaviors (like forming efficient path trails) emerge from simple individual rules.

## 🌟 Features

* **Foraging Logic:** Ants wander randomly until they detect food or a pheromone trail.
* **Pheromone Trails:** Ants carrying food leave a chemical trail (blue) that fades over time. Other ants follow this trail to locate the food source efficiently.
* **Visual State Indicators:**
    * ⚪ **White Ant:** Scouting/Searching for food.
    * 🟢 **Green Ant:** Carrying food back to the colony.
* **High Performance:** Uses a custom **Spatial Partitioning** grid system to efficiently manage collisions and detection for hundreds of entities, ensuring a smooth frame rate.
* **Interactive:** Dynamically add food sources to the environment in real-time.

## 🛠️ Prerequisites

To run this simulation, ensure your environment meets the following requirements:

* **Python Version:** **Python 3.11 or earlier** is required.
    * *Note: Newer versions (like 3.12+) may have compatibility issues with Pygame on certain operating systems.*
* **Dependencies:** You need the `pygame` library.

## 🚀 Installation & Running

1.  **Download the Script:**
    Save the simulation code as `Sim.py`.

2.  **Install Pygame:**
    Open your terminal or command prompt and run:
    ```bash
    pip install pygame
    ```

3.  **Run the Simulation:**
    Navigate to the folder containing the file and execute:
    ```bash
    python Sim.py
    ```

## 🎮 Controls

* **Left Mouse Click:** Spawn a cluster of food (Red dots) at the cursor's location.
* **Close Window:** Exits the application.

## ⚙️ Configuration

You can customize the simulation behavior by opening `Sim.py` in a text editor and modifying the constants at the top of the file:

| Variable | Default | Description |
| :--- | :--- | :--- |
| `NUM_OF_ANTS` | `100` | The total population of the ant colony. |
| `ANT_SPEED` | `1.5` | The movement speed of the ants. |
| `PHEROMONE_STRENGTH` | `100` | How long a trail persists before evaporating. |
| `FOOD_SPAWN_AMOUNT_PER_CLICK` | `40` | Amount of food generated per mouse click. |
| `WIDTH, HEIGHT` | `720` | The resolution of the simulation window. |

## 🧠 Technical Details

### How the Ants Think
1.  **Wander:** If no signals are found, the ant moves randomly.
2.  **Follow:** If a pheromone is detected, the ant adjusts its direction toward the strongest scent.
3.  **Harvest:** Upon touching food (Red), the ant picks it up (turns Green) and heads toward the Anthill.
4.  **Trail:** While carrying food, the ant deposits pheromones. Once at the Anthill (Yellow), it drops the food and returns to "Wander" mode (turns White).

### Optimization
The simulation uses a `Manager` class that implements **Spatial Partitioning**. The screen is divided into a grid (`SPATIAL_PARTITIONING_ROWS` x `COLS`). Ants only calculate distances to food or pheromones within their specific grid tile and immediate neighbors, rather than checking every object in the world. This allows for large numbers of ants and food particles without lagging.

## 📜 License

This project is open-source. Feel free to modify, experiment, and expand upon the code!
