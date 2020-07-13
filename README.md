# Season of Docs Application 
![CV/Portfolio of Tiisetso Mphuthi](http://codewithtiisetso.reacoda.co.za)


### This is my application for season of docs 
##### Below is the sample of two tutorials on using the MicroPython firmware on a NodeMCU dev kit (ESP8266)
## 1. Use MicroPython on Thonny IDE to Blink an LED.
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

##### From the module `time` we get the class `sleep`. This will be used as a timer.

```python
led = Pin(2, Pin.OUT)
```

##### Here we create a Pin object called led. We are using the pin 2 that is where the built-in LED is connected. The pin is also declared as an output device. 

##### Finally we will be using a `while` loop to turn the LED on for half a minute and then turn it off for another half a minute.

### END

## 2. Using Pulse Width Modulation with MicroPython 

##### In this tutorial, we will be using the PWM module from the microPython firmware to control an external LED. This will allow us to control the brightness of the LED.

#### Things that will be Needed:
* NodeMCU dev kit board 
* 220 ohm resistor
* Breadboard
* 5mm LED
* Jumper wires 

#### Setting up the Circuit:

##### The first thing you will need to do is setup the circuit as is shown in the diagram below:

![](https://gblobscdn.gitbook.com/assets%2F-Ly3OADOGtKzS60vUfrw%2F-MBK_z4MqceqfzedtbvL%2F-MBKb6sbb3ljclRK8haU%2FmicroPython(8).PNG?alt=media&token=4d7238fe-26ab-4cee-8743-5c4b3290bdce)

![](https://gblobscdn.gitbook.com/assets%2F-Ly3OADOGtKzS60vUfrw%2F-MBKdI6dqzQu3sZJmDFM%2F-MBKihGoepfdRtiN1YfL%2FNodeMCU_V2_v2.png?alt=media&token=f4da1171-2b03-42ff-94a0-4ab04c9ec1c3)

1. Firstly, on the breadboard insert the LED as shown above.
2. Using a jumper wire connect one end to the long leg of the LED, then connect the other end to the pin D2 on the nodeMCU board.
3. Connect the one end of the 220 ohm resistor to the short leg of the LED as shown above. The other end of the resistor is connected to the GND pin on the nodeMCU board.

#### The Code

##### This is the code that you will write on the editor of Thonny IDE and then upload it to the nodeMCU dev kit board.

```python
from machine import Pin,PWM
from time import sleep

frequency = 5000
led = PWM(Pin(5), frequency)

while True:
  for duty_cycle in range(0, 1024):
    led.duty(duty_cycle)
    sleep(0.005)
```
#### Explaining the Code:

```python
from machine import Pin,PWM
```

##### In this line of code, we get the `Pin` and `PWM` class from the built-in module called `machine`. This is to create the PWM pin.

```python
from time import sleep 
```

##### Here we are getting the `sleep` class from the `time` module. This will be used as a timer.

```python
led = PWM(Pin(5), frequency)
```

##### In this section of the code, we are creating a PWM object that uses the pin that is connected to, the signal frequency, and the duty cycle as its parameters.

##### The *duty* *cycle* can be a value between 0 and 1023. 1023 is the same as 100% duty cycle, which is translated to full brightness (of led). 0 is the same as 0% duty cycle which is unlit led.

##### The frequency can be a value between 0 and 78125. A frequency of 5000 Hz can be used to control the brightness. 

```python
while True:
  for duty_cycle in range(0, 1024):
    led.duty(duty_cycle)
    sleep(0.005)
```

##### Here we use a while loop to set the duty cycle so that we don't need to pass the duty cycle parameter. if we don't set the duty cycle when instantiating the PWM object, it will be 0 by default.

```python
led.duty(duty_cycle)
```

##### To set the duty cycle use the duty() method on the PWM object.

```python
for duty_cycle in range(0, 1024):
    led.duty(duty_cycle)
    sleep(0.005)
```

##### Inside the while loop, we use a for loop that increases the duty cycle by 1 in each loop with an interval of 5 ms between each change.

##### The range() function used above has the following syntax:

```python
range(start, stop, step)
```

##### **start**: a number which specifies at which position to start.
##### **stop**: a number which specifies at which position we want to stop, excluding that value. 
##### **step**: refers to the number of times it iterates

### END



##### The list of my work is included below:
* [Build a Modern Personal Website From Scratch - Part 1](https://medium.com/@tiisetsomphuthi/build-a-modern-personal-website-from-scratch-part-1-24323085624)
* [Build a Modern Personal Website From Scratch - Part 2](https://medium.com/@tiisetsomphuthi/build-a-modern-personal-website-from-scratch-part-2-b968870fa1b7)
* [Build a Modern Personal Website From Scratch - Part 3](https://medium.com/@tiisetsomphuthi/build-a-modern-personal-website-from-scratch-part-3-74cd65ab0fcc)
* [Introduction to Electronics](https://app.gitbook.com/@reacoda/s/molemi-iot/introduction-to-arduino-programming/introduction-to-electronics)
* [Controlling LEDs with an Arduino](https://app.gitbook.com/@reacoda/s/molemi-iot/controlling-leds-with-an-arduino)
* [A light Bulb Switch Using NodeMCU and Blynk](https://app.gitbook.com/@reacoda/s/molemi-iot/introducing-the-nodemcu/a-light-bulb-switch-using-nodemcu-and-the-blynk-app)
