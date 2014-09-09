---
layout: default
title: Module 2- LED Control
date: September 10, 2014
---
A Light Emitting Diode (or LED) is a small electronic component that gives off light when a current is passed through it. LEDs come in many shapes, sizes and colors. Some even have colors that can be varied depending on how they are controlled (such as the RGB LED in your kit).

#### LED Polarity
  First, a word on LED polarity. Some electronics components (including LEDs) are polarized, meaning the direction a component is connected in matters. LEDs have a short leg and a long leg (or a flat side and a round side). The long side (or round side of the plastic shell) should always be connected to the point in the circuit with higher voltage (i.e. higher potential). This will allow current to flow through the LED in the proper direction. 
<img src="https://dl.dropboxusercontent.com/u/1733921/Raspberry%20Pi/LedPolarity.svg" width="50px"/>

###LED Blink Breadboard Layout
The LED should be connected to GPIO Pin 18 as shown in the below diagram. A 560 Ohm resistor is used to limit the current through the LED to 2 mA. A smaller resistor(or none) would allow too much current through the LED and the Raspberry Pi's GPIO port, potentially damaging the port and the LED. 
<img src="https://dl.dropboxusercontent.com/u/1733921/Raspberry%20Pi/Schematics/RaspberryPi-LED%20Blink.png" alt="LED Blink Breadboard Layout" width="300px"/>

#### Why a 560 Ohm resistor?
  The resistor is needed to disspiate extra electrical energy (voltage) coming from the Raspberry Pi. The Pi's digital outputs run at 3.3V and most LEDs have a forward voltage of about 2.2 Volts. As the voltage supply (3.3V) always equals the voltage load (LED + Resistor), our resistor will have a drop of 1.1V across it. We must also keep in mind the current drawn from the Raspberry Pi's output pin. The Raspberry Pi can only source up to 4mA of current, meaning we must choose our resistor to limit the current to less than 4mA at 1.1V.  The current through the LED is determined by an equation known as Ohms Law. It takes the form V=IR, where V is the voltage drop across the resistor, I is the current through the resistor and R is the resistance. We'll use 2mA just to be safe. Using Ohm's Law, we can determine the proper resistance to use is 560 Ohms.<br/>
V=IR<br/>
1.1V = .002A * R<br/>
R=550 Ohms<br/>

  A smaller resistor(or none) would allow too much curren through the LED and the Raspberry Pi's GPIO port, potentially damaging the port and the LED.


# Software Control of the GPIO Port
For the Raspberry Pi to turn the LED on and off, we must be able to control the attached GPIO pin. In the schematic above, this is GPIO pin 18(using Broadcom numbering). To turn pin 18 on or off from a Python script, complete the following steps:

* Import the GPIO library
    {% highlight python %} import RPi.GPIO as GPIO {% endhighlight %}
* Set the GPIO library into Broadcom mode
    {% highlight python %} GPIO.setmode(GPIO.BCM) {% endhighlight %}
* Set the pin as an output
    {% highlight python %} GPIO.setup(18, GPIO.OUTPUT, initial=GPIO.LOW) {% endhighlight %}
* Set the pin to high or low
    {% highlight python %} GPIO.output(18, GPIO.HIGH) {% endhighlight %}
 