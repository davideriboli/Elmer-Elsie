# Elmer & Elsie (*Machina speculatrix*)

A digital simulation and generative art canvas based on W. Grey Walter's cybernetic turtles.

## Historical Background
In 1948 and 1949, at the Burden Neurological Institute in Bristol, neurologist and roboticist William Grey Walter constructed some of the world's first autonomous electronic robots. Named **Elmer** (ELectro MEchanical Robot) and **Elsie** (Electro Light-Sensitive Internal External), Walter classified them under the mock-biological species *Machina speculatrix* due to their speculative, exploring behavior.

Unlike modern programmable robots, Elmer and Elsie had no microprocessor or memory. Their "brains" consisted of purely analogue electronics: two vacuum tubes, a photoelectric cell (sensor for light), and a contact switch (sensor for touch). Despite this extreme simplicity, the continuous interaction between their sensors, their driving/steering motors, and the environment generated complex, emergent behaviors. They exhibited phototaxis (seeking light), obstacle avoidance, and a resting state when the light was adequately bright.

<img width="400" height="489" alt="GreyWalterBlocks" src="https://github.com/user-attachments/assets/772f1b80-0891-4806-af1b-e220fdc2d80e" />

*William Grey Walter watching one of the two original “turtles”<br>as it dodges obstacles on its way home, drawn by the light source inside*.

### The Mirror Experiment
Walter made a groundbreaking observation when he placed a light on the shell of a turtle and allowed it to look into a mirror. The robot's phototropic circuitry reacted to its own reflection, creating a positive feedback loop. The conflicting signals caused the machine to flicker and tremble—a state Walter likened to a rudimentary form of self-recognition and organic hesitation.

## The Digital Simulation
This repository contains a faithful behavioral simulation of Elmer and Elsie, written entirely in Vanilla JavaScript using the HTML5 Canvas 2D API. The goal is not merely visual reproduction, but the emulation of analogue cybernetic feedback loops.

Instead of pre-programmed paths, the digital turtles' movements are strictly dictated by two simulated variables:
*   **Neuron A (Phototropic):** Calculates the delta between the turtle's orientation and the light source, factoring in intensity, distance, and the scanner's rotation angle.
*   **Neuron B (Touch):** Triggers an avoidance routine (backing up and changing angle) when a spatial collision with an obstacle or another turtle is detected.

## Interactive Environment
The simulation features a dynamic, user-manipulable arena:
*   **Light Source:** Can be dragged to test phototropic tracking or reduced to zero intensity to observe aimless wandering.
*   **Obstacles:** Can be dragged via their center mass or rotated via their extended handles.
*   **Touch Stimulus:** Clicking a turtle manually injects a stimulus into Neuron B, forcing an avoidance maneuver.
*   **The Mirror:** Placing the mirror object forces the turtles into Walter's feedback loop if they approach it while scanning. The digital turtle will enter a `frozen` state (trembling).
*   **Relocation:** To break a turtle out of a frozen feedback loop, the user must physically drag and drop the turtle to a new location.

## Generative Art Mode (Trails)
By enabling the **Trails** toggle, the simulation transforms into a generative art canvas. The visual memory of the turtles is significantly extended, leaving a smooth, slowly fading kinetic trace. 

The colors of the trails are not static; they dynamically map to the real-time cognitive state of the artificial brain:
*   **Green/Amber:** Scanning (Default wandering).
*   **Bright Yellow:** Seeking (Locked onto the light source).
*   **Saturated Orange:** Hesitating (Threshold between seeking and freezing).
*   **Deep Red:** Avoiding (Collision detected, evasive maneuver).
*   **Neon Cyan:** Frozen (Locked in the mirror/agent feedback loop).
*   **Warm Grey:** Resting (Satiated by the light source).

## Technical Implementation
*   **Zero Dependencies:** Built strictly with standard web technologies (HTML, CSS, JS). No external frameworks like p5.js or Three.js were used.
*   **Responsive Architecture:** Environmental coordinates are mapped using normalized vectors (`0.0` to `1.0`). Absolute positions are mathematically recalculated only on window resize or drag events, ensuring stable topological aspect ratios without layout distortion.
*   **Performance:** Spatial distance checks for collision and feedback triggers use squared distance comparisons (`dst2`) rather than calculating square roots at every frame, significantly reducing CPU load during the 60 FPS rendering cycle.

## References
1. Walter, W. G. (1950). *An imitation of life*. Scientific American, 182(5), 42-45.
2. Walter, W. G. (1953). *The Living Brain*. W. W. Norton & Company.
