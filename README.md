# Season of Docs Application 
### This is my application for season of docs 
##### Below is the sample of a tutorial on using the MicroPython firmware on a NodeMCU dev kit (ESP8266)
### Use MicroPython on Thonny IDE to Blink an LED.
##### In this tutorial, we will be setting and using microPython firmware on the Thonny IDE.

#### Components Needed 
* Windows OS desktop/laptop computer
* Thonny IDE installed
* MicroPython Firmware installed 
* NodeMCU dev kit and a USB cable 

#### Getting Started.

##### To start programming on your NodeMCU (esp8266) using Thonny IDE, you will need to open the Thonny IDE and then click on **Tools** > **Options** and select the **Interpreter** tab.

##### On the options, choose the Micropython (esp8266)  and then choose the port name (number ) to which your nodeMCU dev board is connected. In this case we chose COM11.
![Setting up MicroPython on Thonny IDE](https://gblobscdn.gitbook.com/assets%2F-Ly3OADOGtKzS60vUfrw%2F-MBFAS71IOLtyxOUusXS%2F-MBFB2iyumxsX3I0Sxbw%2FmicroPython(3).PNG?alt=media&token=d0aa51c2-7658-46cc-a97e-f20333b46b91)

##### Thonny should now be connected to your NodeMCU board and you should the following message on the shell window.

![](https://gblobscdn.gitbook.com/assets%2F-Ly3OADOGtKzS60vUfrw%2F-MBFEoVCaZNql75DVCKr%2F-MBFFIp1DLrb15hwL9jk%2FmicroPython(5).PNG?alt=media&token=d57ba602-4fa7-4a35-8890-c75e2fe14611)

##### To test the configuration, type the command help() and see what you get in response. when everything is in order you should see the following.

![](https://gblobscdn.gitbook.com/assets%2F-Ly3OADOGtKzS60vUfrw%2F-MBFFz1IYEUPBtlLGUmZ%2F-MBFGTdcHK-0aAFXcv6A%2FmicroPython(6).PNG?alt=media&token=26e6d098-1a95-4150-a294-cc84697b2b0f)

#### Testing MicroPython

##### Write the following commands on the Thonny IDE and execute them to light up the on-board LED 

```python
from machine import Pin
Pin(2, Pin.OUT).value(0)
```
##### When using the esp8266 board, the logic works in the opposite. That is to say, the value () argument will be 0 instead of 1 which is usually reserved for "ON".

#### Blinking the built-in LED

##### In this section, we will be programming the nodeMCU board to blink it's built-in LED. The following script will be run on the Thonny IDE's editor.

##### N.B. when uploading the code as ledblink.py it will be saved as main.py on the board regardless of what you saved it as on your computer. 

##### Once you are done uploading the code press the Reset (RST) button on the board.

#### Explanation of the code:

```python
from machine import Pin
```

##### Here we are importing a module called `machine` and from it we are accessing the `Pin` class.

```python
from time import sleep
```

##### From the module `time` we get the class `sleep`.

##### The list of my work is included below:
* [Build a Modern Personal Website From Scratch - Part 1](https://medium.com/@tiisetsomphuthi/build-a-modern-personal-website-from-scratch-part-1-24323085624)
* [Build a Modern Personal Website From Scratch - Part 2](https://medium.com/@tiisetsomphuthi/build-a-modern-personal-website-from-scratch-part-2-b968870fa1b7)
* [Build a Modern Personal Website From Scratch - Part 3](https://medium.com/@tiisetsomphuthi/build-a-modern-personal-website-from-scratch-part-3-74cd65ab0fcc)
* [Introduction to Electronics](https://app.gitbook.com/@reacoda/s/molemi-iot/introduction-to-arduino-programming/introduction-to-electronics)
* [Controlling LEDs with an Arduino](https://app.gitbook.com/@reacoda/s/molemi-iot/controlling-leds-with-an-arduino)
* [A light Bulb Switch Using NodeMCU and Blynk](https://app.gitbook.com/@reacoda/s/molemi-iot/introducing-the-nodemcu/a-light-bulb-switch-using-nodemcu-and-the-blynk-app)
