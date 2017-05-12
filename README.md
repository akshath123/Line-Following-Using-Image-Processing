# Line Following Using Image Processing

Image processing uses lot of computatiion power and it is very slow when implemented with the conventional algroithms for 
line following further it becomes even slower when implemented in embedded boards such as Raspberry pi and Beaglebone as the 
clock speed of such microprocessors is around 1 Ghz to 1.2 Ghz as of 12<sup>th</sup> May 2017. But this algorithm is different 
from the rest as with minimual computation the task is achieved. 

### Asumptions Made

 1. The left hand side and the right hand side of the line is of same colour and the line colour is darker than the arena's color (hue of the line is stronger than the arena's color).
 2. The surface is not glossy and there is no bumps on the surface.
 3. 

### Logic of the algorithm

  **step 1:** Take the frame in BGR value (has OpenCV takes the input as BGR value instead of RBG value)
  **step 2:** Convert the imgae to binary image using otsu's adaptive-threasholding.
  **step 3:** Now the image would be converted to black and white. The line will be in white where as the background will be black.
  **step 4:** Fix the y axsis and run a linear search for finding the first white pixel and then from then on find the first black
              pixel. 
  **step 5:** Those two corrdinates is the location of the line in the frame.
  **step 6:** Divide the frame into half and if the both the coordinate are lying on left of the divider then the camera is 
              moving towards right ( the camera might be mounted on the bot ) and if the both pixel coordinate is lying to the 
              right then the camera is moving left. Change the movement of the bot accordling to bring back on line.
  **step 7:** If the coordinates is located at either sides of the divider then the camera is said to be moving straight. 
  **step 8:** Repeat steps 1-7 for each and every frame captured. 
  
### Improvements can be made

  1. If we go for multi core-programming then the system can go even faster.
  2. If the algorithm is integrated with PID line controller algorithm then there will be less deviations.

 
