# Procedural-Generation-System

## Disclaimer

This is only a showcase of the system being implemented, and the source code will not be provided as it is a system being included in my project that is planned to be released commercially.

## Objective

The objective is to develop a top-down procedurally generated pixel image/visualization that resembles natural landmasses. The visualization must also display different climates and temperatures represented by different colours. The below image shows an example of Iceland that the natural landmass should more or less represent:

<img width="550" height="400" alt="image" src="https://github.com/user-attachments/assets/f4f3e88d-33e0-4e04-b942-e66dc5538020" />

## Observation

The difficults stems from two problems:
1. The visualization must be procedurally generated. This means that data must be fed into an algorithm to produce the image. Nothing should be manually created by me.
2. It must also be perceived as a natural landmass, meaning that there should be temperatures, climates, mountains, and different landforms represented through colours.

To solve this problem, I must use an algorithm that assigns values to a grid, such that each cell in the grid can be coloured in 

## Solution

to solve the first problem, I decided to use a famous procedural generation algorithm known as Perlin Noise. This algorithm takes random noise and transforms it into a noise gradient that can be manipulated to my liking.

<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/443652d4-0ad1-4dd8-be8c-52207d45e806" />
