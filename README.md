## Arduino Stopwatch

Lucas and I have put together a stopwatch program for the Arduino. The program runs inside of the Arduino program on the computer and when Button 1 is pushed the timer will start and then if it is pushed again it will stop the timer and the program will print out the time that the program ran for. There is also a second button, Button 2, that will print out the time that last ran when the stopwatch is stopped. When the stopwatch is started, a red LED is lit up. When the stopwatch is stopped, the green LED is lit up. 
<img src="images\SerialMonitor.png">

## Link to Arduino Code

This is the Repository for the code: [Link](https://github.com/johnslw26/MarcusLucasStopwatch) 

### Code Description

The most important variables are the startResetBTN and elapsedButton they are set to pins 4 and 3 respectively. To make the LED's work we needed to assign them a pin in the code, we named them redLed and greenLed (pins 2 and 8). We ran into an issue which prevented us from using just buttonState to determine if the button is being pressed, it allowed the button to be long pressed which would toggle the states every second (due to the debounce). We fixed this by adding a variable called lastButtonState which is checked later in the code. Now we look at the setup method which includes all the pinMode method calls so that we can determine the pin to be set as an input and output. We initialize the serial monitor to be set at 9600 baud and then print the directions out to it. The loop then contains the core logic of the application. We first declare the initial button state which then we check to lastButtonState (initialized as 10 so it's different). Then lastButtonState is set and we check if the button's voltage is HIGH to determine if it's pushed. We used a variable called isRunning so that we can use one button for two functions, if it isn't running it will start the stopwatch. If it is running it will stop it then set the led lights and set isRunning to false so we can start a new time trial, vice versa for if it's not running. We then display the results through displayResults with a 1 second delay so it doesn't output the same result multiple times. Display time converts the milliseconds into hours, minutes, and seconds. We use a println function to show the results and concatenate them, while converting them to a string. Finally, the function that controls the state of the LED lights, simply put it switches between the red and green lights with input for high or low voltage.

### Project Images

<img src="images\IMAG0676.jpg" width="480" height="480"> 
<img src="images\TestCodePicture1.png" width="480" height="480"> 
--This photo depicts just a single button wired up, in this step we are testing to determine if the button is wired correctly. We jump from the 5v to the positive portion of the breadboard and do the same with ground (red and black). Throughout this project black will show the side that goes to ground, and the colors will be the hot wire.

<img src="images\Snapchat-2062159838.jpg" width="480" height="480"> 
--The button is wired correctly to provide the LED with power, now it's time to figure out how to wire it so that we can run code to shut it on and off rapidly.

<img src="images\Snapchat-1354926983.jpg" width="480" height="480"> 
--This is the initial design, we relocated it so that the buttons and led had space to be used.

<img src="images\Snapchat-1522802363.jpg" width="480" height="480"> 
--We added one more LED (RED) to show that the stopwatch was currently running, when red it means it is counting time. When green it it's ready to be used again.

<img src="images\WonderingWhy.png" width="480" height="480"> 
--We had encountered a major issue that we couldn't resolve, Marcus then noted that we forgot to set the pin to an output pin. The issue was that the LED was very dim, we wired it to multiple pins and tested it without having it connected to the breadboard. We then tried just plain power going positive to negative and it had a normal illumination. 
<img src="images\Snapchat-83336043.jpg" width="480" height="480"> 

<video width="320" height="240" controls>
  <source src="images\Snapchat-1490889450.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>
--We came across an issue regarding button state, it seemed that even though we included a 1 second delay if the user held the button it continued to cycle through the stopwatch's states (used and not used). Lucas proposed a debounce mechanism that records the previous state of the button, and then each loop compares to see if this new state is the same as the last. This worked great, and now the states are independent from one another through the pressing of the button.
<video width="320" height="240" controls>
  <source src="images\Snapchat-1068240847.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

## Final Notes
<img src="images\working.gif">
We managed to get it to work in the most basic form, if we are able to a screen would be a nice addition instead of running it through the serial monitor. The difficult part of adding a screen is finding a compatible LCD screen that doesn't require a bunch of parts that we do not own.
