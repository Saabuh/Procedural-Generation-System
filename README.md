# Procedural-Generation-System

## Disclaimer

This is only a showcase of a system being implemented in my commercial game, and the source code will not be provided as it is a system being included in my project that is planned to be released commercially.

## Objective

The objective is to develop a top-down procedurally generated pixel image/visualization that resembles natural landmasses and can be generated uniquely for each user of the game. This is to ensure each user gets a unique environment and experience without interference from . The visualization must display different climates and temperatures represented by different colours. The below image shows an example of Iceland that the natural landmass should more or less represent:

<img width="550" height="400" alt="image" src="https://github.com/user-attachments/assets/f4f3e88d-33e0-4e04-b942-e66dc5538020" />

## Observation

The difficults stems from two problems:
1. The visualization must be procedurally generated. This means that data must be fed into an algorithm to produce a unique image each time. Nothing should be manually created by me.
2. It must also be perceived as a natural landmass, meaning that there should be temperatures, climates, mountains, and different landforms represented through colours.

To solve this problem, I must use an algorithm that assigns values to a grid, such that each cell in the grid can be coloured in. Example below: 

[0] [0] [0] [1] [1] [1] [1] [0]  
[0] [0] [1] [1] [2] [2] [1] [0]  
[0] [1] [1] [2] [2] [2] [1] [0]  
[1] [1] [2] [2] [3] [2] [1] [0]  
[1] [2] [2] [3] [3] [2] [1] [0]  
[1] [2] [2] [2] [2] [1] [0] [0]  
[0] [1] [1] [1] [1] [0] [0] [0]  
[0] [0] [0] [0] [0] [0] [0] [0]  

then, as a very rough example, assign them as such:  
0 = water  
1 = sand  
2 = grassland  
3 = mountain  

we can keep this in mind for the next section for explaining the algorithm.

## Solution

to solve the first problem, I decided to use a famous procedural generation algorithm known as Perlin Noise. This algorithm takes random noise and transforms it into a noise gradient that can be manipulated to my liking. See the difference betweeen these images:

<img width="600" height="250" alt="image" src="https://github.com/user-attachments/assets/bae0870d-c10a-4dac-bbbe-8584c9a4b21d" />

Both images assign values normalized between 0.0-1.0 on a grid which is then read by the computer to assign colours. Typically, 0 = Black and 1 = White. The image on the right is random noise, which provides no value to us as it doesnt resemble anything. However, the image on the left is perlin noise which creates a gradient between the cells, which somewhat resembles land if we take subsections of it and make black = land and white = water. We will use this as the basis of solving the problem.

Referring back to the grid in Observation, if we normalize the values to be between 0.0-1.1 and assigns colours based on a threshold the cell value falls into, say:

< 0.1 = water  
\> 0.1, < 0.2 = sand  
\> 0.2, < 0.5 = grass  
\> 0.5 = mountains  

we should get an image resembling something like a landmass, like such:

<img width="600" height="350" alt="image" src="https://github.com/user-attachments/assets/5e6b6ce3-7727-4af1-af77-f8fe3e39955e" />

we can see that instead of black and white gradients produced by the perlin noise algorithm, we instead took its gradient value and assigned it a colour based on the thresholds listed previously. Furthermore, to represent different climates/temperature, another perlin noise layer was added - seperate from the first one - that solely represents biomes based on temperature and climate and assigned colours on a new threshold:

< 0.1 = ocean (the blue cells)
\> 0.1, < 0.2 = beaches (the brown cells)
\> 0.2, < 0.3 = desert (the dark brown cells)
\> 0.3, < 0.5 = grasslands (the dark green cells)
\> 0.5 = grasslands (the white cells)

thresholds were picked by me, however they can be tweaked to get more unique biomes and landforms. 



