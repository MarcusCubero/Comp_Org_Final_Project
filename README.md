## Arduino Stopwatch

Lucas and I have put together a stopwatch program for the Arduino. The program runs inside of the Arduino program on the computer and when Button 1 is pushed the timer will start and then if it is pushed again it will stop the timer and the program will print out the time that the program ran for. There is also a second button, Button 2, that will print out the time that last ran when the stopwatch is stopped. When the stopwatch is started, a red LED is lit up. When the stopwatch is stopped, the green LED is lit up. 

### Code Description

The most important variables are the startResetBTN and elapsedButton they are set to pins 4 and 3 respectively. To make the LED's work we needed to assign them a pin in the code, we named them redLed and greenLed (pins 2 and 8). We ran into an issue which prevented us from using just buttonState to determine if the button is being pressed, it allowed the button to be long pressed which would toggle the states every second (due to the debounce). We fixed this by adding a variable called lastButtonState which is checked later in the code. Now we look at the setup method which includes all the pinMode method calls so that we can determine the pin to be set as an input and output. We initialize the serial monitor to be set at 9600 baud and then print the directions out to it. The loop then contains the core logic of the application. We first declare the initial button state which then we check to lastButtonState (initialized as 10 so it's different). Then lastButtonState is set and we check if the button's voltage is HIGH to determine if it's pushed. We used a variable called isRunning so that we can use one button for two functions, if it isn't running it will start the stopwatch. If it is running it will stop it then set the led lights and set isRunning to false so we can start a new time trial, vice versa for if it's not running. We then display the results through displayResults with a 1 second delay so it doesn't output the same result multiple times. Display time converts the milliseconds into hours, minutes, and seconds. We use a println function to show the results and concatenate them, while converting them to a string. Finally, the function that controls the state of the LED lights, simply put it switches between the red and green lights with input for high or low voltage.

### Project Images

<img src="images\working.gif">

<img src="images\Snapchat-83336043.jpg">

<img src="images\Snapchat-135492683.jpg">

<img src="images\Snapchat-1522802363.jpg">

<img src="images\Snapchat-2062159838.jpg">

<img src="images\SerialMonitor.PNG">

<img src="images\Snapchat-1068240847.mp4">

<img src="images\Snapchat-1490889450.mp4">

<img src="images\TestCodePicture1.PNG">

<img src="images\WonderingWhy.PNG">

<img src="images\IMAG0676.jpg">
