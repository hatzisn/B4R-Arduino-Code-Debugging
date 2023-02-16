# B4R-Debugging
Debugging for B4R and Arduino for all microprocessors even the older ones


Tested in Arduino Nano (with old bootloader) and ESP8266.

Add the b4xlib in additional libraries folder. Add the library in the project and use the code that follows. Then compile and when the app starts press disconnect in the logs tab and load the modified code of Anywhere Software's B4R_Serial_Connector in B4J. Run the application connect to the port and press continue as many times as it is required (as seen in the B4R project code). The method is Debug.BP(....) which stands for Break Point and you can pass as an argument the variable you want to see its value or the string you want to display. You can pass all the native types available in B4R (int, long, uint, ulong, string, byte, ubyte, float, double) or null if you don't want it to print anything. It will display the variable value and stop temporarilly the code execution in this line until you press the [Continue] button in the B4J app. In the background, obviously, it does not stop the code execution in the microcontroller, but it gets in an endless loop waiting for input from the serial port and when it gets it, it continues. Thus, it acts like a breakpoint as seen from the outside.
