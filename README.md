# B4R-Debugging
Debugging for B4R and Arduino for all microprocessors even the older ones


Tested in Arduino Nano (with old bootloader) and ESP8266.

Add the b4xlib in additional libraries folder. Add the library in the project and use the code that follows. Then compile and when the app starts press disconnect in the logs tab and load the modified code of Anywhere Software's B4R_Serial_Connector in B4J. Run the application connect to the port and press continue as many times as it is required (as seen in the B4R project code). The method is Debug.BP(....) which stands for Break Point and you can pass as an argument the variable you want to see its value or the string you want to display. You can pass all the native types available in B4R (int, long, uint, ulong, string, byte, ubyte, float, double) or null if you don't want it to print anything. It will display the variable value and stop temporarilly the code execution in this line until you press the [Continue] button in the B4J app. In the background, obviously, it does not stop the code execution in the microcontroller, but it gets in an endless loop waiting for input from the serial port and when it gets it, it continues. Thus, it acts like a breakpoint as seen from the outside.

Here is how it can be used:

B4R:

<pre>
#Region Project Attributes
    #AutoFlushLogs: True
    #CheckArrayBounds: True
    #StackBufferSize: 300
#End Region
'Ctrl+Click to open the C code folder: ide://run?File=%WINDIR%\System32\explorer.exe&Args=%PROJECT%\Objects\Src

Sub Process_Globals
    Public Serial1 As Serial
End Sub

Private Sub AppStart
    Serial1.Initialize(9600)
    Log("AppStart")
    Dim i As Int = 1
    Dim l As Long = 2
    Dim b As Byte = 45
    Dim ui As UInt = 31
    Dim ul As ULong = 32
    Dim f As Float = 51.45
    Dim d As Double = 61.75
 
 
 
    Debug.BP(i)
    Debug.BP(l)
    Debug.BP(b)
    Debug.BP(ui)
    Debug.BP(ul)
    Debug.BP(Null)
    Debug.BP(f)
    Debug.BP(d)
    Debug.BP2(Array As String("The value of the double variable is ", d, " and the value of the float is ", f))
 
    Dim ii As Int = 0
    Log("I start")
    Debug.BP("Just before I add 1 in variable ii")
    ii = ii + 1
    Debug.BP2(Array As String("The value of the ii variable is ", ii))
    ii = ii + 2
    Debug.BP2(Array As String("The value of the ii variable is ", ii))
    ii = ii + 3
    Debug.BP2(Array As String("The value of the ii variable is ", ii))
    Log("Ok Done")
End Sub

</pre>
