# Drawing Robot
This project is a two-wheeled drawing robot that uses an Arduino Nano ESP32, a gyroscope, motor encoders, and servo motors to draw designs on paper in different colors. Throughout this project I learned how hardware and software work together by designing circuits, writing Arduino code, debugging electrical issues, and calibrating the robot to move accurately. 

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Iris Z | Piedmont Hills High School | Electrical Engineering | Incoming Sophomore

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Since my second milestone, my focus has shifted from programming/building the robot to expanding its capabilities through custom mechanical modification. 

Instead of using a single pen that moves up and down, I designed a rotating pen holder that can hold multiple colored pencils. The goal is to allow the robot to switch between colors while drawing, making more complex and colorful artwork. Designing this modification required me to use onShape to CAD my own model. Since I am low on time, I took time outside of camp to brainstorm a simple and easy way to make a rotating pen tube. The criteria are that the pencils are always needed to be up- unless pushed down to draw, and the tube itself also has to rotate. I came up with a circlish design, which looked at carefully, is basically the same as the original design, but inversed. 

the Design: 

Other designs (servo holders and stuff): 

I used 2 servos to make the contraption work. The first is attached to the bottom of the spinning tubes, and it can also precisely measure exactly 0-180 to get the pencil to match with the hole in the arcylic board. The other servo uses another 3D printed design I found online to use its horn to push down the pencils. Unfortunately, I overlooked the fact that servos can only rotate to 180 degrees, and not 360. Since my design uses the full circle, one of the pencils would never be used. 

Through Bluestamp, I have learned a lot about a variety of different topics I haven't even touched on before, developing new passions and skills. Some of which include circuit design, troubleshooting, CAD, and coding with C++. I have coded prior to Bluestamp, and after experiencing the engineering portion of creating. I hope to continue learning more about robotics, hardware, and more advanced engineering projects. Additionally, I decided to prioritize finishing my modifications over perfecting the Gcode callibration. So, I wish to continue working on that even after the program finishes. 


# Second Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

During my second milestone, I wrote code to make the breadboard circuit into a functioning drawing robot. I mounted all of the electronics onto an acrylic board, installed the motors, wheels, pencil lift tube, and glides. Most of my time was spent developing the software that controls the robot.

Assembling the robot wasn't too bad. There were a few notable problems I had to face though. One, finding the perfect height for the glides. Being a 2-wheeled robot, it cannot balance by itself. At the 2 ends of the board (without the wheels) there are glides underneath the board to stabalize the robot. However, if the glides were too tall, the wheels wouldn't create enough friction with the ground to move, but if the glides were too short, there's literally no point in having them. Getting to the right height took meticulous sanding. Two, the motors holders weren't actually holding the robot in place, so the wheels would sometimes steer of course because of a tilt. I used Chase's 3D design to compensate, since it was tighter and properlly secured the wheels. 

Photo of assembled robot: 

One of the biggest parts of this milestone was creating a Wi-Fi control website hosted directly from the Arduino Nano ESP32. Instead of using Bluetooth, I programmed the robot to generate its own webpage where I could send movement commands and display live information from the robot. I added buttons for driving forward, backward, turning, stopping, adjusting speed, and raising or lowering the pen. I also added a calibration system and displayed the robot status directly on the webpage.

A large amount of time was spent debugging and calibrating the robot. There were may times small syntax errors or use of the wrong library caused issues that took me days to fix. For example, switching between analogWrite and digitalWrite might cause the wheels to freeze up, or adding delays on specific Wi-Fi libraries could cause everything to stop running. However, these hurdles I overcame as I program my robot results in a functioning website. The code doesn't include simple movement and turns, but uses an detailed system using the gyroscope and encoder counts to make sure the robot is moving precisely. This required measuring backlash, calculating encoder counts per millimeter, and implementing smoother acceleration and stopping behavior. The code is at the bottom of this webpage in its own section. 

By the end of this milestone, the robot was capable of:
- Driving forward and backward
- Making accurate 90° turns
- Using the gyroscope to maintain a straight heading
- Measuring distance using wheel encoders (used for Gcode)
- Raising and lowering the pen with the servo
- Being controlled through a custom Wi-Fi website
- Beginning to interpret and execute G-code drawings

This milestone taught me much more about programming than I expected. I have learned a bit of coding before, but not C++, so I learned how web servers work on embedded devices, how feedback systems improve accuracy, how to debug effectively, and also a new coding language through coding with the Arduino IDE. 

Getting through milestone 2 was a huge challenge for me: one, because coding was so painstakingly tedious, but mainly because of the many, many, MANY, bugs I faced that were solved by simple solutions everyone overlooks. It wasn't extremely hard, but it ate through my time in the camp. For milestone 3, I plan to add my modification, a way to colors, as well as have the Gcode work properly and consistently. 

A carasoul with the 3d prints and stuff: 


# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/goyVb42py1c?si=6O3a13vubs9H2Tlj" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

For my first milestone, my goal was to get every electronic component working together before building the robot itself. I focused on wiring the entire circuit on a breadboard, testing each component individually, and making sure the Arduino Nano ESP32 could recieve instructions over Wi-Fi.

One of the biggest changes I made from the original project guide was switching several components. I replaced the Arduino Uno with an Arduino Nano ESP32 so the robot could effectively communicate over Wi-Fi instead of Bluetooth. Since the Nano ESP32 already uses 3.3V, I also no longer needed the level shifter that was originally included in the design for the gyroscope and bluetooth communicator. I also had to use an L9110 motor driver to compensate for the missing TB6612FNG motor driver with an L9110 motor driver. This required a little bit of modifying both the wiring (and later software) to match.

Starting the project was on of the hardest part, so after picking up the steam, it was much easier to get a move on. The inital wiring diagram did look complicated, but after researching each part and understanding its function, the circuit slowly began to make much more sense. Moreover, removing the bluetooth module and level shifter greatly simplified the wiring. The diagram is in the schematics section. 

During this milestone I successfully tested the servo motor, DC motors, wheel encoders, gyroscope, voltage regulator (converting 9V battery supply to 6V for powering specific components), and Wi-Fi communication separately before combining everything into one complete circuit. Majority of the hardware was brand new to me, so I learned a lot about how breadboards works, and how each of the components interact within the circuit as well as with the Arduino nano esp 32. I now know each pin has different functins as well, besides just being analog and digital. This milestone gave me a much stronger understanding of electronics and prepared me for the software portion of the project. (My next milestone)

wiring irl: 

# Schematics 
wiring diagram: 
my drawing ig: 
My other drawing maybe:
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
codeeee:
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
My original inspiration is ______. his page is what gave me the boost to start my project off well, and have a general idea of what the circuit and pencil lift contraption should be like. Addionally he provided great insight on the theory of how the code should be written to account for variables such as backlash. 
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
  
I also used the 3D designs of other people for my servo holders, linked below: 
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)
