# Simple Perceptron Visualization

A real-time visualization of a **Single-Layer Perceptron** built with **Processing (Java)**. This project demonstrates the fundamental concepts of neural networks by training a simple model to classify data points into two categories using a linear decision boundary.

## 🧠 Project Overview

The program generates random data points on a 2D plane and attempts to classify them. As the program runs, you witness the "learning" process:

* **The Problem:** Classify points as either *Class A* (White) or *Class B* (Black) based on their position.
* **The Model:** A Perceptron that adjusts its internal weights to find the dividing line.
* **The Visualization:** The model draws its current "best guess" line, which adjusts in real-time until it matches the target separation line.

## 📂 File Structure

The project is split into three files to separate logic, data, and visualization:

| File Name | Description |
| :--- | :--- |
| **`CC_SimplePerceptron.pde`** |**The Main Sketch.** Handles the setup, the draw loop, and the visualization logic. It coordinates the training process by feeding one point per frame to the brain. |
| **`perceptron.pde`** | **The Brain.** Contains the `Perceptron` class. It manages the weights, the activation function, and the core learning algorithms (guessing and training). |
| **`Training.pde`** | **The Data.** Contains the `Point` class for generating random training data and the helper function `f(x)` that defines the target line. |

## ⚙️ How It Works

### 1. The Perceptron
The Perceptron takes three inputs: an $x$ coordinate, a $y$ coordinate, and a fixed **bias**. It calculates a weighted sum of these inputs:

$$\text{Sum} = \sum (Input_i \times Weight_i)$$

It then passes this sum through an **activation function** (`sign`), which turns the output into a binary classification (1 or -1).

### 2. The Training Loop (Supervised Learning)
The system trains incrementally (Stochastic Gradient Descent):

1.  **Guess:** The brain makes a prediction for a given point.
2.  **Calculate Error:** The system compares the guess to the known correct label.
    $$\text{Error} = \text{Target} - \text{Guess}$$
3.  **Update Weights:** The weights are adjusted to correct the error for the next time.
    $$W_{new} = W_{old} + (\text{Error} \times \text{Input} \times \text{Learning Rate})$$

### 3. Visualization Key
* **White/Black Points:** The actual class of the data point.
* **Green Fill:** The Perceptron guessed **correctly**.
* **Red Fill:** The Perceptron guessed **incorrectly**.
* **Moving Line:** Represents the Perceptron's current weights/decision boundary.

## 🚀 Getting Started

1.  **Install Processing:** Download and install the IDE from [processing.org](https://processing.org).
2.  **Setup:** Create a new sketch and ensure all three files (`CC_SimplePerceptron.pde`, `perceptron.pde`, `Training.pde`) are in the same folder.
3.  **Run:** Press the **Play** button.

## 🛠 Customization

You can tweak the values in the code to see how they affect learning:

* **Learning Rate (`lr`):** Found in `perceptron.pde`. Change the default `0.1` to a smaller number for smoother but slower learning, or a larger number for faster but potentially unstable learning.
* **Dataset Size:** Change `Point[] points = new Point[100];` in the main file to train on more or fewer examples.
