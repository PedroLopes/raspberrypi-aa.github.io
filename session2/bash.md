---
layout: default
title: Bash Control of GPIO Ports
date: September 14, 2013
---

##Bash Script Control of GPIO Ports
The Pi's GPIO ports can be controlled from the command line (i.e. bash), python scripts, and C/C++ programs. There are 17 GPIO ports available on the Pi. Some of them have special purposes or special hardware configurations and should be avoided for normal use.

####Using GPIO from bash

The following commands should be run as root (type 'sudo bash' to become root). This code sets up pin 18 to be an output, sets the pin high and then sets it low.

{% highlight bash %}
#   Exports pin to userspace
echo "18" > /sys/class/gpio/export                  

# Sets pin 18 as an output
echo "out" > /sys/class/gpio/gpio18/direction

# Sets pin 18 to high
echo "1" > /sys/class/gpio/gpio18/value

# Sets pin 18 to low
echo "0" > /sys/class/gpio/gpio18/value 

{% endhighlight %}

This next snippet sets up pin 4 to be an input, then reads the value of the input.

{% highlight bash %}
echo "4" > /sys/class/gpio/export
echo "in" > /sys/class/gpio/gpio4/direction
cat /sys/class/gpio/gpio4/value
{% endhighlight %}