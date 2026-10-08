# 3D Pong — Project Showcase

A 3D Pong game built in C for an embedded RISC-V system as a two-person ECE243 project at the University of Toronto, combining software-rendered graphics, VGA output, and PS/2 mouse input.

**Source code remains private because this is course work. This repository is a project showcase.**

## The game

Players control a paddle with a mouse and return a ball as it travels toward and away from the screen. Moving the paddle during contact adds spin, curving the ball's trajectory.

- **Endless mode:** keep the ball in play and build a high score.
- **Levels mode:** face a computer-controlled paddle with increasing difficulty.
- **Software rendering:** a rotating, shaded 20-triangle ball with visual depth cues.
- **Display:** 320 × 240 VGA output with double buffering synchronized to vertical sync.
- **Input:** interrupt-driven PS/2 mouse control.
- **Victory animation:** a rotating, shaded golden coin.
- **Physics:** arcade style, 

## Ilia's contribution

I'm **Ilia Javan**, and I implemented the 3D graphics pipeline:

| Component | Implementation |
| --- | --- |
| Depth projection | Custom fixed-point depth scaling using integer shifts and multiplication |
| Triangle rasterization | Filled projected triangles using a modified Bresenham-style algorithm |
| Object rotation | Quaternion orientation updates and conversion to rotation matrices |
| Mesh rendering | Vertex transformations and triangle-based object rendering |
| Backface culling | Projected triangle winding to skip faces pointing away from the viewer |
| Shading | Face normals and a reference light direction to calculate brightness |

## Khaleel's contribution

I'm **Khaleel Khaki**, and I implemented the core gameplay systems:

| Component | Implementation |
| --- | --- |
| Game loop & state management | Real-time game loop with start, gameplay, win/lose, and restart states |
| Ball physics | Ball movement with spin mechanics and collision detection |
| Paddle control | PS2 mouse interrupt-driven paddle control |
| Enemy AI | Level-based enemy AI with progressively increasing difficulty |
| Scoring | Player scoring and high-score tracking |
| VGA rendering | Start, gameplay, win, and lose screen rendering to the VGA buffer |

## Engineering decisions

**Small mesh geometry.** A 20-triangle ball limited geometry processing while making rotation and shading visible.

**Fixed-point depth scaling.** Integer shifts and multiplication implement the depth effect without floating-point division in the projection functions. Rotation and shading still use floating-point arithmetic.

**Quaternion orientation.** Quaternions track orientation, and rotation matrices transform mesh vertices for rendering.

**Cull before rasterization.** Backface culling avoids filling triangles facing away from the viewer.

**Real-time game loop.** A centralized game loop manages input, physics, collision detection, AI, scoring, and rendering to maintain responsive gameplay.

**Interrupt-driven input.** PS2 mouse interrupts provide responsive paddle control without continuously polling for input.

**Progressive AI difficulty.** Enemy AI increases in difficulty across levels, providing a gradual challenge while maintaining consistent core gameplay mechanics.

**Spin-based ball physics.** Paddle collisions incorporate spin to influence the ball's trajectory and make gameplay more dynamic.


## Teamwork

| Contributor | Responsibilities |
| --- | --- |
| **Ilia Javan** | Depth projection, triangle rasterization, quaternion rotation, mesh rendering, backface culling, and shading |
| **Khaleel Khaki** | Background and screens, game states, ball physics and collisions, PS/2 input, paddle rendering, opponent behavior, and scoring |

We integrated the graphics pipeline with the game logic to display the ball's position and spin during gameplay.

## Technologies

**C · RISC-V · Embedded systems · VGA · PS/2 · Computer graphics · Quaternion mathematics**

The project used CPUlator during development. This showcase contains a high-level description only; it does not include source code, build files, or course documents.
