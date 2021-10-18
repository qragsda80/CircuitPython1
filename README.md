# CircuitPython
 The follwing files are my first foray into CircuitPython.
## Table of Contents
* [Table of Contents](#TableOfContents)
* [Hello_CircuitPython](#Hello_CircuitPython)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_LCD](#CircuitPython_LCD)
* [NextAssignmentGoesHere](#NextAssignment)
---

## Hello_CircuitPython

### Description & Code
Description goes here

Here's how you make code look like code:

```python
import board
import neopixel
import time

dot = neopixel.NeoPixel(board.NEOPIXEL, 1)

dot.brightness=0.2

while True:
    print("Make it Green!")
    dot.fill((0, 255, 0))
    time.sleep(.5)
    print("Make it Blue!")
    dot.fill((0, 0, 255))
    time.sleep(.5)



```


### Evidence
Pictures / Gifs of your work should go here

<img src="HelloCircuitPython.gif" alt="The Wiring" width="500">

### Wiring
Make an account with your google ID at [tinkercad.com](https://www.tinkercad.com/learn/circuits), and use "TinkerCad Circuits to make a wiring diagram."  It's really easy!  
Then post an image here.   [here's a quick tutorial for all markdown code, like making links](https://www.markdownguide.org/basic-syntax/)

<img src="Screenshot 2021-10-17 12.38.49 PM.png" alt="The Wiring" width="500">


### Reflection
What went wrong / was challenging, how'd you figure it out, and what did you learn from that experience?  Your ultimate goal for the reflection is to pass on knowledge that will make this assignment better or easier for the next person.

One thing that went wrong was that I didn't know I had to "Import Time." Once I did that, it worked and it blinked the colors back and forth.


## CircuitPython_Servo

### Description & Code

In this assignment, we used a metro express board, a micro servo, and python coding to make the servo turn 180 degrees and then back 180 degrees. After we firgured that out, we added two loose wires to make capacitive touch controlled. 

```python
import time
import board
import pulseio
import touchio
import servo

# create a PWMOut object on Pin A2.
pwm = pulseio.PWMOut(board.A2, duty_cycle=2 ** 15, frequency=50)

# Create a servo object, my_servo.
my_servo = servo.Servo(pwm)

touch_pad1 = board.A0  # Will not work for Circuit Playground Express!
touch1 = touchio.TouchIn(touch_pad1)
touch_pad2 = board.A5  # Will not work for Circuit Playground Express!
touch2 = touchio.TouchIn(touch_pad2)

while True:

    if touch1.value:
        print("Touched the White Wire!")
        for angle in range(0, 180, 5):  # 0 - 180 degrees, 5 degrees at a time.
            my_servo.angle = angle
            time.sleep(0.05)
    if touch2.value:
        print("Touched the Green Wire!")
        for angle in range(180, 0, -5):  # 180 - 0 degrees, 5 degrees at a time
            my_servo.angle = angle
            time.sleep(0.05)
    time.sleep(0.05)
    print("end of loop!")

```

### Evidence

<img src="ezgif.com-gif-maker.gif" alt="The Wiring" width="500">

### Wiring

<img src="Screenshot 2021-09-16 093200.png" alt="The Wiring" width="500">

### Reflection

This assignment helped me learn about the python coding language. The hardest part of this assignment was the touch capacitive part. I struggled finding the right code, but Callan and Mr. Helmstetter helped me figure it out. For other people trying this assignment I would recommend having friends around to ask and using all of the tools around you. 




## CircuitPython_LCD

### Description & Code

```python
import time
import board
import neopixel
import simpleio
import adafruit_hcsr04

sonar = adafruit_hcsr04.HCSR04(trigger_pin=board.D2, echo_pin=board.D3)
dot = neopixel.NeoPixel(board.NEOPIXEL, 1)

r = 0
cm = 0
while True:
    try:
        cm = sonar.distance
        print((cm))
        if cm < 5:
            r = 255
            g = 0
            b = 0
            print("red!")
        elif cm < 20:
            print("red or blue")
            r = simpleio.map_range(cm, 5, 20, 255, 0)
            g = 0 
            b = simpleio.map_range(cm, 5, 20, 0, 255)
        
        elif cm < 35:
            print("blue or green")
            r = 0
            g = simpleio.map_range(cm, 20, 35, 0, 255)
            b = simpleio.map_range(cm, 20, 35, 255, 0)
        else:
            print("green")
        dot.fill((int(r), int(g), int(b)))
        
    except RuntimeError:
        print("Retrying!")
    time.sleep(0.1)

```

### Evidence

<img src="ultrasonicsensor.gif" alt="The Wiring" width="500">

### Wiring

### Reflection





## NextAssignment

### Description & Code

```python
Code goes here

```

### Evidence

### Wiring

### Reflection
