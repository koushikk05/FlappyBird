# Flappy Bird Game - README

## Overview

This project is a simple implementation of the popular game *Flappy Bird* using Java and Swing for the graphical interface. The game involves a bird that the player controls by pressing the spacebar to keep it from falling. The bird must navigate between two sets of pipes that move from right to left. The game ends when the bird collides with a pipe or the ground.

## Project Structure

### App.java
This is the main class that sets up the game window and runs the game loop. It initializes the frame, the size of the board, and adds the FlappyBird panel to the window.

#### Key components:
- **JFrame**: A `JFrame` is created to display the game window, set to a fixed size of 360x640 pixels, and the FlappyBird panel is added to it.
- **Visibility**: The window is centered on the screen and is set to be non-resizable.

### FlappyBird.java
This class contains the core game logic, drawing, and interactions. It extends `JPanel` and implements `ActionListener` and `KeyListener` to handle user input and update the game state.

#### Key Components:
- **Game Board**:
  - **Board Dimensions**: `boardWidth` = 360, `boardHeight` = 640
  - **Images**: Background, bird, and pipe images are loaded into the game.
  
- **Bird Class**:
  - The bird is represented by a `Bird` object, which includes properties for position, size, and an image. It is controlled by user input (spacebar for jump).
  - **Physics**: The bird’s vertical movement is influenced by gravity, and it can "jump" by setting its vertical velocity to -9 when the spacebar is pressed.

- **Pipe Class**:
  - Pipes are represented by a `Pipe` object, each having an `x` and `y` position, width, height, and an image. They move from right to left across the screen at a constant velocity (`velocityX` = -4).
  - When the bird passes a pipe set (top and bottom pipe), the score is increased by 0.5 (to account for both pipes in a set).

- **Game Logic**:
  - The `move()` method updates the bird’s position and the movement of pipes.
  - **Collision Detection**: A collision check is performed between the bird and the pipes using the `collision()` method. If a collision is detected, the game ends.
  - **Score**: The score increases as the bird successfully passes pipes.

- **Timers**:
  - **Game Loop**: The game loop is controlled using a `Timer` which repeatedly calls `actionPerformed()` to update the game state (move pipes, update bird position, repaint).
  - **Pipe Placement Timer**: A separate timer is responsible for generating new pipes at regular intervals.

- **Key Event Handling**:
  - The `keyPressed()` method listens for the spacebar key press to make the bird jump.
  - When the game is over, pressing space restarts the game by resetting all relevant variables (bird position, velocity, score, pipes).

## Game Features

- **Bird Movement**: The bird’s movement is controlled by gravity and jump mechanics (spacebar).
- **Pipes**: Pipes are generated at regular intervals and move from right to left. The player must avoid collisions with them.
- **Score**: The score increases as the bird successfully passes sets of pipes.
- **Game Over**: The game ends when the bird collides with a pipe or falls below the ground.
