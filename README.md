# Competing Game of Life: A New Interpretation

This project implements a variation on John Conway's classic Game of Life cellular automaton, introducing multiple competing "species" or colors of cells with unique interaction rules. It runs entirely in a web browser using JavaScript and the HTML5 Canvas API.

## Description

Based on the foundational rules of Conway's Game of Life, this simulation introduces three distinct cell colors (White, Red, Blue) that compete for space on the grid. The core mechanics are reinterpreted:

* **Survival:** Cells survive based on the standard Game of Life rules (2 or 3 neighbors) but *only* considering neighbors of their **own color**.
* **Birth:** Dead cells come alive if they have exactly 3 neighbors of **one specific color**.
* **Interaction (Retaliation):** When a cell is born, it causes one randomly chosen neighboring cell of an **opposing color** to die in the next generation. Cells do *not* die simply from being adjacent to an opposing color otherwise.

This creates dynamic and evolving patterns as the different colors compete and interact.

## Features

* **Multi-Color Simulation:** Simulates three distinct cell types (White, Red, Blue) plus dead cells.
* **Competing Ruleset:** Implements unique survival, birth, and interaction (retaliation) rules.
* **Large Grid Support:** Optimized using `ImageData` for efficient rendering of large grids (e.g., 1600x1200).
* **Interactive Spawning:** Click on the canvas to spawn a circular cluster of cells with random colors based on initial probabilities.
* **Configurable:** Key parameters like grid size, simulation speed, spawn radius, and initial color probabilities can be adjusted within the script.
* **Browser-Based:** Runs directly in any modern web browser with no server-side requirements or external libraries (besides the browser's built-in Canvas API).

## How to Run

1.  Save the code from the `<immersive>` block with the id `game_of_life_js` as an HTML file (e.g., `competing_gol.html`).
2.  Open the saved HTML file in your web browser.
3.  The simulation will start automatically.
4.  Click anywhere on the canvas to spawn new cells in a circular area.

## Configuration

The following constants can be modified near the top of the `<script>` tag within the HTML file to change the simulation's behavior:

* `GRID_WIDTH`, `GRID_HEIGHT`: Dimensions of the simulation grid (and the canvas).
* `CLICK_SPAWN_RADIUS`: The radius (in cells/pixels) of the spawn area created on click.
* `UPDATE_INTERVAL_MS`: The target time in milliseconds between simulation steps (lower is faster).
* `INITIAL_PROBABILITIES`: An array defining the probability of each active color appearing during initial grid setup and click-spawning. The order corresponds to `WHITE`, `RED`, `BLUE`. The sum should ideally be <= 1.0 (the remainder is the probability of a `DEAD` cell).
* `STATE_COLORS_RGBA`: Defines the RGBA colors used for rendering each state.
