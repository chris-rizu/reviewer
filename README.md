# Final Exam Reviewer

Based on:

- `05_Intro-to-Arduino_NS.pdf`
- `Arduino-Motors.pdf`
- `07_Behavioral-Modeling_NS.pdf`
- `08_Combinational-Logic-Circui_NS.pdf`
- `09_Sequential-Logic-Circuit_NS.pdf`
- `10_UDP-Tasks-and-Functions_NS.pdf`

This reviewer is written as a teaching guide, not just a summary. It follows the topics from the PDFs and explains them in beginner-friendly language.


Memory rule:

- `Arduino`: think `hardware + wiring + code + signal flow`
- `HDL`: think `inputs -> logic behavior -> output -> timing`

---

# SUBJECT 1: MICROPROCESSOR

## 1. Intro to Arduino

### 1.1 What Arduino is

Arduino is an open-source electronics platform built to make prototyping easier. It was created so students, hobbyists, artists, and beginners could quickly build interactive systems without needing deep hardware experience first.

Main ideas from the lesson:

- Arduino is both hardware and software.
- The hardware is the board, such as the Arduino Uno.
- The software is the Arduino IDE where you write and upload code.
- It is beginner-friendly because the programming style is simple and transferable to C/C++-style thinking.

Memory aid:

- `Arduino = Board + IDE + Sketch + Sensors/Actuators`

### 1.2 Why Arduino became popular

The slides emphasize that Arduino became the "go-to gear" for:

- artists
- hobbyists
- students
- makers
- rapid prototyping

Why?

- low cost
- easy USB programming
- reusable libraries
- simple pin-based I/O
- lots of examples and shields

### 1.3 Arduino Uno board overview

The reviewer slides point out the main Uno features:

- USB connection for programming and serial communication
- power jack
- voltage regulator
- ATmega328 microcontroller
- digital I/O pins
- analog input pins
- PWM-capable pins
- reset button
- serial communication pins

Important pins/features to remember:

- `Digital pins 0-13`
- `Analog pins A0-A5`
- `PWM pins` are usually marked with `~`
- common PWM pins on Uno: `3, 5, 6, 9, 10, 11`
- pins `0` and `1` are also used for serial communication, so use them carefully

### 1.4 The ATmega328 microcontroller

The ATmega328 is the "brain" of the Arduino Uno.

What it does:

- reads input signals from sensors and switches
- processes logic based on your program
- drives outputs like LEDs, buzzers, and motors

Simple mental model:

- `input -> processing -> output`

Exam tip:

- If asked what really executes the program, the answer is not "the Arduino board" in a vague sense. The exact chip doing the work is the `ATmega328 microcontroller`.

### 1.5 Arduino shields

The slides show shields as stackable add-on boards.

Examples shown:

- Micro SD
- MP3 Trigger
- LCD

Purpose of shields:

- add extra features without building the circuit from scratch
- plug on top of the Arduino board

Think of a shield as:

- `an expansion board for a specific purpose`

### 1.6 Breadboard basics

The breadboard is used to build circuits without soldering.

Key lesson points:

- a single LED can be wired using a breadboard and resistor
- the LED must be connected with correct polarity
- the resistor limits current to protect the LED

LED polarity:

- longer leg = positive = anode
- shorter leg = negative = cathode

Resistor value shown in the lesson:

- `330 ohms`
- color code mentioned: `orange-orange-brown`

Why the resistor is needed:

- without it, too much current may flow
- the LED can burn out
- the Arduino pin can also be stressed

### 1.7 Inputs vs outputs

This is one of the most important Arduino ideas.

From the perspective of the microcontroller:

- `Input` means a signal goes into the board
- `Output` means a signal leaves the board

Examples of inputs from the slides:

- buttons
- switches
- light sensors
- flex sensors
- humidity sensors
- temperature sensors

Examples of outputs from the slides:

- LEDs
- DC motor
- servo motor
- piezo buzzer
- relay
- RGB LED

Memory aid:

- `Input = sensing`
- `Output = acting`

### 1.8 Digital vs analog

The slides contrast these clearly.

Digital:

- only discrete states
- usually `HIGH/LOW`
- often treated as `1/0`

Analog:

- can take a range of values
- example: light intensity, temperature level, potentiometer position

Important Arduino reality:

- the microcontroller is fundamentally digital
- analog-like output is simulated using `PWM`

### 1.9 Arduino IDE

The Arduino IDE is where you:

- write code
- verify/compile code
- upload code
- open serial monitor
- choose the board
- choose the serial port

Settings stressed in the slides:

- `Tools -> Board`
- `Tools -> Serial Port`

Why these matter:

- if the wrong board is selected, compilation/upload may fail
- if the wrong serial port is selected, the PC cannot talk to the Arduino

### 1.10 The two required functions

Every basic Arduino sketch has:

```cpp
void setup() {
}

void loop() {
}
```

Meaning:

- `setup()` runs once when the board powers on or resets
- `loop()` runs again and again forever

Beginner memory aid:

- `setup = one-time preparation`
- `loop = repeated behavior`

### 1.11 Comments in Arduino code

The slides strongly remind students to use comments.

Single-line comment:

```cpp
// this is a single-line comment
```

Multi-line comment:

```cpp
/* this is
   a multi-line comment */
```

Why comments matter:

- explain your intent
- make debugging easier
- help your classmates and future self understand the code

### 1.12 Three commands you must know

The lesson highlights:

```cpp
pinMode(pin, INPUT/OUTPUT);
digitalWrite(pin, HIGH/LOW);
delay(time_ms);
```

Explanation:

- `pinMode()` sets whether a pin is used to read or send signals
- `digitalWrite()` sends `HIGH` or `LOW` to an output pin
- `delay()` pauses the program for a number of milliseconds

Example:

```cpp
pinMode(13, OUTPUT);
digitalWrite(13, HIGH);
delay(2500);
```

Meaning:

- set pin 13 as output
- turn it on
- wait 2.5 seconds

Important note:

- Arduino commands are case-sensitive

### 1.13 Blink: the "Hello World" of physical computing

This is the first practical circuit.

Typical blink sketch:

```cpp
void setup() {
  pinMode(13, OUTPUT);
}

void loop() {
  digitalWrite(13, HIGH);
  delay(1000);
  digitalWrite(13, LOW);
  delay(1000);
}
```

Line-by-line explanation:

- `pinMode(13, OUTPUT);`
  configures digital pin 13 to drive a device
- `digitalWrite(13, HIGH);`
  sends 5V-like logic high so the LED turns on
- `delay(1000);`
  waits 1000 ms = 1 second
- `digitalWrite(13, LOW);`
  turns the LED off
- `delay(1000);`
  waits another second

What the hardware is doing:

- current flows from the pin through the resistor and LED
- LED lights when the voltage difference is correct

Possible exam variations:

- faster blink
- heartbeat blink
- multiple LEDs
- Morse code pattern

### 1.14 Variables and variable types

Variables store data used by the program.

The slides mention scope:

- global variable: declared outside functions, accessible broadly
- local variable: declared inside a function, exists only there

Types listed in the lesson:

- `byte`
- `int`
- `long`
- `char`
- `unsigned int`
- `unsigned long`
- `float`

Exam tip:

- know the difference between `global` and `local`
- know that variable choice affects memory and range

### 1.15 PWM and fading

The fading lesson teaches that some pins can simulate analog output.

Important concept:

- `PWM = Pulse Width Modulation`

PWM idea:

- the pin rapidly turns on and off
- changing the ON-time percentage changes the average voltage
- this changes apparent brightness or motor speed

Duty cycle meaning:

- higher duty cycle -> more average power
- lower duty cycle -> less average power

The lesson specifically notes:

- use PWM pins such as `3, 5, 6, 9, 10, 11`
- `analogWrite(pin, value)` takes a value from `0` to `255`

Interpretation:

- `0` -> always off
- `255` -> always on
- middle values -> partially on, giving intermediate average output

### 1.16 Fade example, line by line

The slide OCR shows the standard Fade sketch logic.

A cleaned version:

```cpp
int led = 9;
int brightness = 0;
int fadeAmount = 5;

void setup() {
  pinMode(led, OUTPUT);
}

void loop() {
  analogWrite(led, brightness);
  brightness = brightness + fadeAmount;

  if (brightness == 0 || brightness == 255) {
    fadeAmount = -fadeAmount;
  }

  delay(30);
}
```

Explanation:

- `int led = 9;`
  chooses PWM pin 9
- `int brightness = 0;`
  starts from fully dark
- `int fadeAmount = 5;`
  changes brightness by 5 each cycle
- `analogWrite(led, brightness);`
  outputs the PWM brightness value
- `brightness = brightness + fadeAmount;`
  increases or decreases brightness
- `if (brightness == 0 || brightness == 255)`
  checks whether the LED reached either extreme
- `fadeAmount = -fadeAmount;`
  reverses direction of change
- `delay(30);`
  controls how fast the fading happens

Exam-style understanding:

- changing `delay()` changes speed
- changing `fadeAmount` changes step size
- using two LEDs with opposite brightness produces a cross-fade effect

### 1.17 RGB LED

The slides introduce the RGB LED as a tri-color LED.

Important hardware note from the lesson:

- the sample kit used a `common cathode RGB LED`
- the longest leg goes to `GND`

Why RGB works:

- it contains `red`, `green`, and `blue` LEDs in one package
- each color intensity can be controlled separately
- mixing intensities creates many colors

The slide states the color count idea as:

- `256 x 256 x 256 = 16,777,216` possible color combinations

### 1.18 RGB code example

The lesson shows three PWM pins:

```cpp
int redPin = 5;
int greenPin = 6;
int bluePin = 9;

void setup() {
  pinMode(redPin, OUTPUT);
  pinMode(greenPin, OUTPUT);
  pinMode(bluePin, OUTPUT);
}

void loop() {
  analogWrite(redPin, 255);
  analogWrite(greenPin, 255);
  analogWrite(bluePin, 255);
}
```

What this does:

- sends maximum intensity to all three channels
- on a common cathode RGB LED, that produces white or near-white light

How to create colors:

- red only: `(255, 0, 0)`
- green only: `(0, 255, 0)`
- blue only: `(0, 0, 255)`
- yellow: `(255, 255, 0)`
- cyan: `(0, 255, 255)`
- magenta: `(255, 0, 255)`

### 1.19 High-current loads and transistor idea

The slides briefly transition from LEDs to motors/high-current loads and mention an NPN transistor common-emitter driver.

Why this is important:

- Arduino pins cannot safely drive many motors or heavy loads directly
- a transistor acts like an electronic switch
- the Arduino pin controls the transistor
- the transistor handles the larger current

Exam concept:

- `Arduino pin controls, external source powers load`

### 1.20 Inputs and digital sensors

The slides define input as any signal entering an electrical system.

Digital sensor examples:

- pushbutton
- switch

A pushbutton produces a digital state:

- pressed or not pressed
- logic `HIGH` or `LOW`

### 1.21 Pull-up resistor

The switch lesson includes pull-up resistor behavior.

Why a pull-up is needed:

- without it, the input can float
- floating inputs give unreliable random values

Pull-up idea:

- when the button is not pressed, the resistor keeps the pin at a defined logic level
- when the button is pressed, the input changes to the opposite level through the switch path

Arduino shortcut:

- `INPUT_PULLUP` can be used internally for many button circuits

### 1.22 Reading digital input

The key command is:

```cpp
digitalRead(pin)
```

Typical pattern:

```cpp
int buttonState = digitalRead(5);
```

Meaning:

- read the logic state from pin 5
- store it in `buttonState`

Possible values:

- `HIGH`
- `LOW`

### 1.23 Conditional statements with buttons

The slides connect button input with `if()` logic.

Example concept:

```cpp
int buttonState = digitalRead(5);

if (buttonState == HIGH) {
  // do something
} else {
  // do something else
}
```

What this teaches:

- the program changes behavior based on input
- this is the foundation of interactive systems

### 1.24 Potentiometer / trimpot

The lesson introduces a potentiometer as a variable resistor.

Structure:

- one fixed end
- another fixed end
- one movable wiper

Why it matters:

- turning the knob changes resistance ratio
- this produces a changing voltage
- Arduino can read that voltage with an analog pin

### 1.25 Basic Ohm's law and voltage divider idea

The slides mention the voltage divider rather than only the simple `V = IR` form.

Big exam idea:

- a potentiometer often works as a voltage divider
- the wiper gives a fraction of the supply voltage
- Arduino reads that varying voltage

Simple recall:

- `Ohm's Law: V = I R`

Voltage divider meaning in words:

- the input voltage is split across resistors
- the output voltage depends on the resistor ratio

### 1.26 Serial communication

The slides define serial communication as a method of transferring data between two devices.

In Arduino:

- the computer and Arduino communicate through USB serial
- Serial Monitor is used to observe values and debug

Why this is useful:

- you can print sensor values
- you can verify logic states
- you can troubleshoot code and hardware

Common commands to know:

```cpp
Serial.begin(9600);
Serial.print("text");
Serial.println(value);
```

Explanation:

- `Serial.begin(9600);` starts serial communication at 9600 baud
- `Serial.print()` prints without new line
- `Serial.println()` prints and goes to the next line

### 1.27 analogRead and analog sensors

Analog sensors produce a range of values.

Examples from the slides:

- microphone -> sound volume
- photoresistor -> light level
- potentiometer -> dial position

Command:

```cpp
analogRead(A0)
```

Meaning:

- reads the voltage on analog pin `A0`
- converts it into a numeric value

Exam tip:

- know the difference between `digitalRead()` and `analogRead()`
- `digitalRead()` gives discrete state
- `analogRead()` gives a range

### 1.28 Serial troubleshooting

The slides end with serial troubleshooting examples, such as printing pin values.

Typical idea:

```cpp
Serial.print("Digital pin 9: ");
Serial.println(value);
```

Why examiners like this:

- it shows you understand debugging
- it proves you can inspect what the program is actually reading or writing

### Most Likely to Appear in the Exam: Intro to Arduino

- Difference between `input` and `output`
- Difference between `digital` and `analog`
- Purpose of `setup()` and `loop()`
- Commands: `pinMode`, `digitalWrite`, `digitalRead`, `analogRead`, `analogWrite`, `delay`
- Why a resistor is used with an LED
- PWM and why `analogWrite()` is not true analog output
- RGB LED common cathode wiring
- Pushbutton logic with `if`
- Potentiometer as a voltage divider
- Serial Monitor for debugging

---

## 2. Arduino Motors

### 2.1 DC motor basics

A DC motor is one of the most common motors. It usually has:

- one positive lead
- one negative lead

If connected directly to a battery:

- it spins in one direction

If the leads are reversed:

- it spins in the opposite direction

### 2.2 How a DC motor works

The slide explains this through magnetic interaction.

Core principle:

- like poles repel
- unlike poles attract

Important motor parts named in the lesson:

- armature: coil of wire
- stator: permanent magnet structure

How rotation happens:

1. current flows through the coil
2. the coil becomes an electromagnet
3. magnetic forces act between coil and stator
4. torque is produced
5. the motor rotates

### 2.3 Speed control using PWM

The lesson directly connects motor speed to applied average voltage.

PWM idea for motors:

- use ON-OFF pulses
- the average voltage changes with duty cycle

Duty cycle meaning:

- larger duty cycle -> larger average voltage -> higher speed
- smaller duty cycle -> smaller average voltage -> lower speed

This is exactly the same PWM idea used in LED fading, but the effect is speed instead of brightness.

### 2.4 Direction control using H-Bridge

To reverse a DC motor, you reverse the polarity across the motor.

The lesson explains that an H-Bridge:

- has four switches
- places the motor in the center
- can drive current in either direction through the motor

Why it is called H-Bridge:

- the circuit arrangement looks like the letter `H`

Important exam idea:

- `PWM controls speed`
- `H-Bridge controls direction`

### 2.5 Servo motor basics

The slides define a servo as a closed-loop control system.

That means:

- the system uses feedback
- it adjusts motion to reach a desired position

Inside a hobby servo:

- small DC motor
- gears
- control electronics
- output shaft

### 2.6 How hobby servos are controlled

The lesson explains control using pulses.

Key facts:

- a pulse arrives roughly every `20 ms`
- this is around `50 Hz`
- pulse width determines position

Typical values from the slides:

- around `0.5 ms` to `2.5 ms` depending on brand
- common midpoint example: `1.5 ms`

General interpretation:

- shorter pulse -> smaller angle
- longer pulse -> larger angle

### 2.7 Servo wiring

One slide shows servo connector color conventions from brands like Futaba and Hitec.

You should remember the three servo connections:

- power
- ground
- signal

Common exam-safe way to say it:

- `Red = Vcc`
- `Black/Brown = GND`
- `White/Yellow/Orange = signal`

### 2.8 Servo library

The slides discuss the `Servo` library in detail.

To use it:

```cpp
#include <Servo.h>
Servo myservo;
```

Meaning:

- include the library
- create a servo object

Important note from the slides:

- on many boards, using the Servo library disables PWM on pins `9` and `10`

### 2.9 `attach()` method

Syntax:

```cpp
servo.attach(pin);
servo.attach(pin, min, max);
```

Meaning:

- connect the servo object to an Arduino pin
- optional `min` and `max` define pulse widths in microseconds

Slide values:

- default minimum: `544 us`
- default maximum: `2400 us`

Example:

```cpp
#include <Servo.h>
Servo myservo;

void setup() {
  myservo.attach(9);
}

void loop() {
}
```

### 2.10 `write()` method

Syntax:

```cpp
servo.write(angle);
```

Meaning:

- on a standard servo, it sets the angle
- on a continuous rotation servo, it controls speed/direction tendency

Example from the lesson:

```cpp
myservo.write(90);
```

Meaning:

- standard servo goes to midpoint
- continuous servo tends toward stop around center

### 2.11 `writeMicroseconds()`

Syntax:

```cpp
servo.writeMicroseconds(us);
```

The lesson explains:

- `1000 us` -> fully counter-clockwise
- `1500 us` -> middle
- `2000 us` -> fully clockwise

It also warns:

- some manufacturers respond in a wider range like `700` to `2300`
- pushing beyond endpoints can cause a high-current condition

This is a favorite exam question because it tests whether you know the low-level control method.

### 2.12 `read()`, `attached()`, `detach()`

`read()`:

- returns the last angle written

`attached()`:

- checks if the servo object is attached to a pin

`detach()`:

- disconnects the servo object from the pin
- may free PWM functionality again on certain pins

### 2.13 Stepper motor basics

The lesson defines a stepper motor as a motor that moves in discrete steps.

Why this matters:

- very precise motion control
- accurate positioning
- widely used in printers, CNC machines, and 3D printers

Key property:

- a full revolution is divided into equal angular steps

### 2.14 Stepper motor types

The slides mention:

- variable reluctance
- permanent magnet
- hybrid
- bipolar
- unipolar

For exam purposes, the most common practical comparison is:

- `unipolar`
- `bipolar`

### 2.15 Unipolar vs bipolar

Unipolar:

- easier drive arrangement
- current direction through coil sections is handled differently

Bipolar:

- usually needs current reversal through windings
- commonly uses a driver/H-bridge style approach

### 2.16 Stepper phases and drive modes

The slides explain that coils are grouped into phases and energized in sequence.

Three important drive modes:

1. Single coil excitation / wave drive
2. Double coil excitation / full step
3. Half step drive

#### Wave drive

- only one coil energized at a time
- lowest power
- lowest torque

#### Full step

- two coils energized together
- more power
- high torque

#### Half step

- alternates between single-coil and double-coil states
- smoother motion
- more step positions

Memory aid:

- `wave = weak`
- `full = stronger`
- `half-step = smoother and finer`

### 2.17 Stepper sample code idea

The slides show code using:

- arrays of output pins
- drive patterns
- state updates
- `analogRead(A0)` for delay/speed control
- `digitalRead(3)` as a direction/control input

Core logic concept:

```cpp
for (int i = 0; i < 4; i++) {
  d = (pattern >> i) & 1;
  digitalWrite(s[i], d);
}
```

What this means:

- each bit of a pattern determines whether a coil pin is HIGH or LOW
- the program shifts through patterns to rotate the motor

This is important because it connects software state patterns to physical coil energizing.

### 2.18 Stepper library

The lesson presents:

```cpp
Stepper(steps, pin1, pin2)
Stepper(steps, pin1, pin2, pin3, pin4)
```

Meaning:

- create a stepper motor object
- specify the number of steps per revolution
- specify the drive pins

Key formula from the slide:

- if degrees per step is known, then:
- `steps per revolution = 360 / degrees per step`

Example:

- `360 / 3.6 = 100 steps`

### 2.19 `setSpeed(rpms)` and `step(steps)`

`setSpeed(rpms)`:

- sets the rotation speed in RPM
- does not move the motor by itself

`step(steps)`:

- moves the motor by a specific number of steps
- positive steps -> one direction
- negative steps -> opposite direction

Important note from the slide:

- `step()` is blocking
- the program waits until the motion completes

Why this matters in exams:

- if the speed is very low and steps are many, the program may appear frozen because it is still busy stepping

### 2.20 EEPROM basics

The lesson ends with EEPROM.

EEPROM means:

- `Electrically Erasable Programmable Read-Only Memory`

Key properties:

- non-volatile
- data remains even after reset or power-off
- used for small permanent storage

Uno fact from the slide:

- ATmega328 has `1024 bytes` of EEPROM

Other values mentioned:

- `512 bytes` for ATmega168
- `4096 bytes` for ATmega2560

### 2.21 EEPROM limitations

Each address stores:

- one byte
- values `0` to `255`

Write endurance from the slide:

- around `100,000 write/erase cycles` per position

Exam tip:

- EEPROM is not for endless rapid writing
- use it when you need settings or saved values across power cycles

### 2.22 EEPROM library

To include:

```cpp
#include <EEPROM.h>
```

Functions listed in the lesson:

- `read()`
- `write()`
- `update()`
- `get()`
- `put()`
- `EEPROM[]`

### 2.23 `read()` and `write()`

`read()`:

```cpp
EEPROM.read(address)
```

- reads one byte

`write()`:

```cpp
EEPROM.write(address, value)
```

- writes one byte

Important note:

- an EEPROM write takes about `3.3 ms`

### 2.24 `update()`

```cpp
EEPROM.update(address, value)
```

Why it is better than `write()` sometimes:

- writes only if the new value is different
- saves write cycles

### 2.25 `put()` and `get()`

`put()`:

- writes a whole data type or object

`get()`:

- reads a whole data type or object

These are more convenient than manually splitting bytes when storing larger structured data.

### 2.26 `EEPROM[]` array style

The lesson shows EEPROM can be accessed like an array:

```cpp
unsigned char val;
val = EEPROM[0];
EEPROM[0] = val;
```

This is a simple shorthand for reading/writing a cell.

### Most Likely to Appear in the Exam: Arduino Motors

- DC motor direction changes by reversing polarity
- PWM controls DC motor speed
- H-Bridge controls motor direction
- Servo uses pulse width, usually around 20 ms period
- Servo library methods: `attach`, `write`, `writeMicroseconds`, `read`, `attached`, `detach`
- Stepper motor moves in discrete steps
- Stepper drive modes: wave, full-step, half-step
- Formula: `steps per revolution = 360 / degrees per step`
- EEPROM is non-volatile
- Difference between `write()` and `update()`

---

# SUBJECT 2: HDL

## 3. Behavioral Modeling

### 3.1 Main idea

Behavioral modeling describes what a circuit does rather than drawing gates explicitly.

The lesson objectives include:

- behavioral structures
- procedural constructs
- initial blocks
- always blocks
- blocking and nonblocking assignments
- timing controls
- selection constructs
- loop constructs

### 3.2 Behavioral modeling structures

The slides list:

- continuous assignment
- blocking procedural assignment `=`
- nonblocking procedural assignment `<=`
- procedural continuous assignment
- `assign ... deassign`
- `force ... release`
- selection structures
- iterative structures

Very important distinction:

- `continuous assignment` is usually used for combinational logic outside procedural blocks
- `blocking` and `nonblocking` are procedural assignments inside `initial` or `always`

### 3.3 Procedural constructs

The slides say all procedures are specified within:

- `initial`
- `always`
- `task`
- `function`

Big meaning:

- behavioral code runs inside procedures
- tasks/functions are reusable procedures called from other procedures

### 3.4 `initial` block

An `initial` block:

- starts at simulation time `0`
- executes exactly once
- is often used to initialize signals or for testbench control

Example:

```verilog
reg x, y, z;
initial begin
  x = 1'b0; y = 1'b1; z = 1'b0;
  #10 x = 1'b1; y = 1'b1; z = 1'b1;
end
```

Explanation:

- initialize values at time 0
- after 10 time units, update them

Important:

- multiple `initial` blocks all start at time 0
- they run concurrently

### 3.5 `always` block

An `always` block:

- starts at simulation time `0`
- executes continuously
- models repeated hardware behavior

Classic clock generator example:

```verilog
reg clock;
initial clock = 1'b0;
always #5 clock = ~clock;
```

Explanation:

- clock starts at 0
- every 5 time units, invert clock
- full period is 10 time units

Very important rule from the slides:

- `initial` and `always` blocks cannot be nested

### 3.6 Procedural assignments

These must be inside `initial` or `always`.

General forms:

```verilog
variable_lvalue = [timing_control] expression;
[timing_control] variable_lvalue = expression;
```

Possible left-hand side targets:

- `reg`
- `integer`
- `real`
- `time`
- memory word
- bit-select
- part-select
- concatenation

Bit-width rule from the slides:

- if RHS is wider, it is truncated
- if RHS is narrower, zeros are filled into upper bits

### 3.7 Blocking assignment `=`

Blocking assignments:

- execute in order
- later statements wait for earlier ones

Example:

```verilog
initial begin
  x = #5 1'b0;
  y = #3 1'b1;
  z = #6 1'b0;
end
```

Timeline:

- `x` gets assigned at time 5
- then `y` is assigned 3 time units later, so at time 8
- then `z` is assigned 6 time units later, so at time 14

Memory aid:

- `blocking = one after another`

### 3.8 Nonblocking assignment `<=`

Nonblocking assignments:

- do not block following procedural statements
- are used for concurrent-style updates
- are the preferred style for sequential logic

Example:

```verilog
initial begin
  x <= #5 1'b0;
  y <= #3 1'b1;
  z <= #6 1'b0;
end
```

Timeline:

- `y` changes at time 3
- `x` changes at time 5
- `z` changes at time 6

The statements are scheduled independently.

Memory aid:

- `nonblocking = schedule first, update together by event timing`

### 3.9 Blocking vs nonblocking in shift registers

The lesson uses shift-register examples to show when the two styles matter.

Correct sequential style:

```verilog
always @(posedge clk) begin
  qout[0] <= sin;
  qout[1] <= qout[0];
  qout[2] <= qout[1];
  qout[3] <= qout[2];
end
```

Why correct:

- all right-hand sides are read before updates happen
- data shifts one stage per clock edge

Incorrect blocking-style shift chain:

```verilog
always @(posedge clk) begin
  qout[0] = sin;
  qout[1] = qout[0];
  qout[2] = qout[1];
  qout[3] = qout[2];
end
```

Why dangerous:

- the new value can ripple through in one clock event in simulation
- that does not match intended register behavior

Exception noted in the slides:

- a vector assignment like `qout = {qout[2:0], sin};` may still behave correctly because the RHS is evaluated before assignment

### 3.10 Race conditions

The slides show:

```verilog
always @(posedge clock) x = y;
always @(posedge clock) y = x;
```

This has a race condition with blocking assignments because execution order can affect results.

Better version:

```verilog
always @(posedge clock) x <= y;
always @(posedge clock) y <= x;
```

Why no race:

1. read RHS values
2. evaluate expressions
3. update LHS values

That matches hardware behavior better.

### 3.11 Coding rule for assignments

The slide gives the most important RTL coding rule:

- use `<=` for sequential logic
- use `=` for combinational logic

This rule is extremely exam-worthy.

### 3.12 Timing controls

Timing controls determine when statements execute in simulation.

Types covered:

- delay control
- event control
- `posedge`
- `negedge`
- event OR control

#### Delay control

Uses `#`

Example:

```verilog
#10 a = b;
```

Meaning:

- after 10 time units, assign `b` to `a`

#### Event control

Uses `@`

Example:

```verilog
@(posedge clk) q <= d;
```

Meaning:

- perform the assignment when a positive clock edge occurs

### 3.13 `posedge` and `negedge`

`posedge`:

- 0 to 1 transition

`negedge`:

- 1 to 0 transition

These are critical for sequential logic modeling.

### 3.14 Selection constructs

Covered in the slides:

- `if`
- `if ... else`
- `case`
- `casex`
- `casez`

#### `if ... else`

Best for:

- priority-style logic
- simple decisions

#### `case`

Best for:

- one selected action out of many exact matches

#### `casex`

- treats `x` and `z` as don't-cares

#### `casez`

- treats `z` as don't-care

Exam warning:

- `casex` can hide unknowns too aggressively, so be careful

### 3.15 Loop constructs

The lesson covers:

- `while`
- `for`
- `repeat`
- `forever`

#### `while`

- repeats while condition is true

#### `for`

- controlled loop with initialization, condition, update

#### `repeat`

- repeats a fixed number of times

#### `forever`

- endless loop

Common use:

- clock generation in testbenches

### Most Likely to Appear in the Exam: Behavioral Modeling

- Difference between `initial` and `always`
- Difference between blocking `=` and nonblocking `<=`
- Why nonblocking is used in sequential logic
- Race conditions
- Delay control `#` and event control `@`
- `posedge` and `negedge`
- `if/case/casex/casez`
- Loop constructs: `while`, `for`, `repeat`, `forever`

---

## 4. Combinational Logic Circuit

### 4.1 Main idea

Combinational logic output depends only on present input values.

No memory:

- same input now -> same output now

Modules listed in the lesson:

- decoder
- encoder
- priority encoder
- multiplexer
- demultiplexer
- comparator
- adder/subtractor
- multiplier
- PLA
- parity generator

### 4.2 Ways to model combinational logic

The slides list several styles:

- Verilog primitives
- continuous assignment
- behavioral statement
- function
- task without delay/event control
- combinational UDP
- interconnection of modules

### 4.3 Three descriptions of combinational logic

The lesson maps logic descriptions to Verilog styles:

- circuit schematic -> structural model
- truth table -> UDP
- switching equations -> continuous assignment

This is a useful conceptual exam question.

### 4.4 Decoder

A decoder has:

- `n` input lines
- `m` output lines

Each output corresponds to one minterm of the input.

Key idea:

- exactly one output is selected for each input combination in a full decoder

Total decoding:

- `m = 2^n`

### 4.5 2-to-4 decoder

For two inputs `x[1:0]`, the outputs are:

- `00 -> y0 active`
- `01 -> y1 active`
- `10 -> y2 active`
- `11 -> y3 active`

The slides show both active-low and active-high forms.

#### Active-low decoder example

```verilog
module decoder_2to4_low(x, enable, y);
input [1:0] x;
input enable;
output reg [3:0] y;

always @(x or enable)
  if (!enable) y = 4'b1111;
  else
    case (x)
      2'b00: y = 4'b1110;
      2'b01: y = 4'b1101;
      2'b10: y = 4'b1011;
      2'b11: y = 4'b0111;
      default: y = 4'b1111;
    endcase
endmodule
```

Meaning:

- active output is driven `0`
- all inactive outputs stay `1`

#### Active-high decoder example

```verilog
if (!enable) y = 4'b0000;
else
  case (x)
    2'b00: y = 4'b0001;
    2'b01: y = 4'b0010;
    2'b10: y = 4'b0100;
    2'b11: y = 4'b1000;
    default: y = 4'b0000;
  endcase
```

Meaning:

- active output becomes `1`

### 4.6 Parameterized decoder

The slides show a parameterized decoder.

Key ideas:

- parameters make modules reusable
- `m` = input width
- `n` = output width

Important line:

```verilog
y = {{n-1{1'b0}}, 1'b1} << x;
```

Meaning:

- start with value `...0001`
- shift left by `x`
- the selected output bit becomes 1

### 4.7 Encoder

An encoder does the opposite of a decoder.

It converts:

- one active input line

into:

- binary code on the output

Important problem pointed out by the slides:

- ordinary encoders have many undefined cases if more than one input is active

### 4.8 4-to-2 encoder

Basic mapping:

- `0001 -> 00`
- `0010 -> 01`
- `0100 -> 10`
- `1000 -> 11`

Any other pattern can be undefined or `x`.

The slides show both `if...else` and `case` implementations.

### 4.9 Priority encoder

A priority encoder resolves multiple active inputs by choosing the highest-priority one.

Example from the slides:

- input 3 has highest priority
- then input 2
- then input 1
- then input 0

Example logic:

```verilog
if (in[3]) y = 3;
else if (in[2]) y = 2;
else if (in[1]) y = 1;
else if (in[0]) y = 0;
else y = 2'bx;
```

The slides also include `valid_in`:

- indicates whether any input is active at all

### 4.10 Parameterized priority encoder

The lecture uses loops:

- `for`
- `while`

Purpose:

- scan from highest bit to lowest bit
- output the index of the first `1`

Why an `else` assignment is needed in combinational logic:

- to avoid inferred latches
- every output must be assigned for every possible condition

### 4.11 Multiplexer

A multiplexer selects one of many inputs and forwards it to a single output.

Definition:

- `m-to-1 mux` has `m` inputs, one output, and enough select lines to choose one input

For a 4-to-1 mux:

- 4 inputs
- 2 select lines
- 1 output

### 4.12 4-to-1 mux example

The slides show a clean conditional operator implementation:

```verilog
assign y = select[1] ?
           (select[0] ? in3 : in2) :
           (select[0] ? in1 : in0);
```

Step-by-step:

- if `select[1] = 1`, choose from upper pair `in3/in2`
- otherwise choose from lower pair `in1/in0`
- then `select[0]` picks the final one

### 4.13 Mux with enable

If enable is off:

- output goes to zero or inactive state defined by the design

If enable is on:

- selected input appears at output

### 4.14 Mux using `case`

The slides also show:

```verilog
case (select)
  2'b11: y = in3;
  2'b10: y = in2;
  2'b01: y = in1;
  2'b00: y = in0;
endcase
```

This is a common exam coding pattern.

### 4.15 Demultiplexer

A demultiplexer does the opposite of a multiplexer.

It takes:

- one input

and routes it to:

- one of many outputs

The others remain zero/inactive.

For a 1-to-4 demux:

- one input
- two select lines
- four outputs

### 4.16 Demux example

The lecture uses repeated `if...else` style:

```verilog
if (select == 3) y3 = in; else y3 = 0;
if (select == 2) y2 = in; else y2 = 0;
if (select == 1) y1 = in; else y1 = 0;
if (select == 0) y0 = in; else y0 = 0;
```

Why this works:

- exactly one output receives the input
- all others are explicitly cleared

### 4.17 Comparator

The slides define magnitude comparator as a device that compares two numbers.

Possible results:

- `A > B`
- `A = B`
- `A < B`

Exam understanding:

- equality comparator checks whether all bits match
- magnitude comparator determines which operand is greater

### Most Likely to Appear in the Exam: Combinational Logic

- Decoder vs encoder
- Active-high vs active-low decoder
- Why a plain encoder has undefined cases
- Priority encoder and `valid_in`
- 4-to-1 mux truth/selection behavior
- 1-to-4 demux behavior
- Why combinational blocks need all outputs assigned
- Parameterized modules and why they are useful

---

## 5. Sequential Logic Circuit

### 5.1 Main idea

Sequential logic depends on:

- present input
- previous state

So unlike combinational logic, it has memory.

The slides say sequential logic is modeled using:

- edge-sensitive `always` blocks

And the normal coding style is:

- use nonblocking assignments

### 5.2 Common sequential modules

Listed in the lesson:

- synchronizer
- finite state machine
- sequence detector
- data register
- shift register
- register file
- counters

### 5.3 Asynchronous reset D flip-flop

Example:

```verilog
module DFF_async_reset(clk, reset_n, d, q);
input clk, reset_n, d;
output reg q;

always @(posedge clk or negedge reset_n)
  if (!reset_n) q <= 0;
  else q <= d;
endmodule
```

Meaning:

- `q` updates to `d` on clock rising edge
- but if `reset_n` goes low, output resets immediately

Why called asynchronous:

- reset does not wait for clock edge

### 5.4 Synchronous reset D flip-flop

Example:

```verilog
always @(posedge clk)
  if (reset) q <= 0;
  else q <= d;
```

Meaning:

- reset is checked only on clock edge

Difference to remember:

- asynchronous reset acts immediately
- synchronous reset acts only when the triggering clock edge arrives

### 5.5 Inferred latch

The slides warn about unintentional latches.

Example cause:

```verilog
always @(din or le)
  if (le == 1'b1)
    dout = din;
```

Why latch is inferred:

- when `le` is not 1, `dout` is not assigned
- so the old value must be held

Three causes listed in the slides:

1. `if` without `else`
2. incomplete `case`
3. incomplete sensitivity list for simulation

This is very important.

### 5.6 Data register

Basic N-bit register:

```verilog
module register(clk, din, qout);
parameter N = 4;
input clk;
input [N-1:0] din;
output reg [N-1:0] qout;

always @(posedge clk)
  qout <= din;
endmodule
```

Meaning:

- on each rising clock edge, store `din` into `qout`

### 5.7 Register with asynchronous reset

```verilog
always @(posedge clk or negedge reset_n)
  if (!reset_n) qout <= {N{1'b0}};
  else qout <= din;
```

Key notation:

- `{N{1'b0}}` means replicate `0` N times
- used to clear all bits at once

### 5.8 Register with load and reset

The lecture shows:

```verilog
always @(posedge clk or negedge reset_n)
  if (!reset_n) qout <= {N{1'b0}};
  else if (load) qout <= din;
  else qout <= qout;
```

Why the final line is called redundant:

- in a sequential element, if nothing is assigned on a clock edge, the register naturally keeps its old value
- so explicitly writing `qout <= qout;` is not necessary

### 5.9 Register file

The lesson presents:

- one write port
- two read ports

Key ideas:

- memory is stored as an array
- reads are selected by read addresses
- write occurs on clock edge if enabled

Important code concept:

```verilog
assign douta = reg_file[rd_addra];
assign doutb = reg_file[rd_addrb];

always @(posedge clk)
  if (wr_enable) reg_file[wr_addr] <= din;
```

Meaning:

- reads are combinational
- write is sequential

### 5.10 Synchronous RAM

The slides show RAM modeled as a memory array.

Core idea:

```verilog
always @(posedge clk)
  if (cs)
    if (wr) ram[addr] <= din;
    else dout <= ram[addr];
```

Interpretation:

- if chip select is active:
- and `wr = 1`, perform a write
- otherwise perform a read

Important warning from the slides:

- `else` matches the nearest previous unmatched `if`

So indentation alone is not enough.

Use `begin ... end` when needed to force grouping.

### 5.11 Shift registers

The lesson covers format conversion:

- `SISO`
- `SIPO`
- `PISO`
- `PIPO`

Meanings:

- `SISO`: serial in, serial out
- `SIPO`: serial in, parallel out
- `PISO`: parallel in, serial out
- `PIPO`: parallel in, parallel out

### 5.12 Basic shift register

Example:

```verilog
always @(posedge clk or negedge reset_n)
  if (!reset_n) qout <= {N{1'b0}};
  else qout <= {din, qout[N-1:1]};
```

Meaning:

- shift right
- new serial input enters one side
- previous bits move over by one position

### 5.13 Shift register with parallel load

```verilog
always @(posedge clk or negedge reset_n)
  if (!reset_n) qout <= 0;
  else if (load) qout <= din;
  else qout <= {sin, qout[N-1:1]};
```

Operation:

- reset clears it
- if `load` is high, load full parallel data
- otherwise shift normally

### 5.14 Universal shift register

The slides describe a universal shift register as one that can:

- hold/no change
- shift right
- shift left
- parallel load

Typical control mapping from the slide:

- `00` -> no change
- `01` -> shift right
- `10` -> shift left
- `11` -> parallel load

This is a very common theory question.

### 5.15 Ripple counter

Ripple counter is asynchronous:

- output of one stage clocks the next stage

Important effect:

- stages do not all change at exactly the same instant
- transitions ripple through

### 5.16 Synchronous binary counter

A synchronous counter updates all bits from the same clock edge.

Example concept:

```verilog
always @(posedge clk)
  if (reset) qout <= 0;
  else if (enable) qout <= qout + 1;
```

Meaning:

- reset clears count
- if enabled, increment

### 5.17 Carry output

The slides show:

```verilog
assign cout = &qout;
```

Meaning:

- reduction AND of all bits
- `cout` becomes 1 only when all bits of `qout` are 1

Why useful:

- indicates terminal count
- can be used for cascading counters

### 5.18 Up/down counter

An up/down counter:

- increments if control selects up
- decrements if control selects down

The exam may ask you to explain how one control bit changes the arithmetic operation.

### 5.19 Modulo-r counter

A modulo-r counter counts:

- `0` up to `r-1`
- then wraps around

This is another common exam question.

Example:

- modulo-10 counter counts `0` to `9`, then returns to `0`

### 5.20 Johnson counter

A Johnson counter is a shift-register-based counter with feedback.

Typical features:

- produces a repeating pattern sequence
- useful in sequence generation

Even if your exam does not ask for detailed derivation, know that it is different from a normal binary counter.

### Most Likely to Appear in the Exam: Sequential Logic

- Asynchronous vs synchronous reset
- Why incomplete combinational code causes inferred latch
- Register, register file, synchronous RAM basics
- Shift register types: SISO, SIPO, PISO, PIPO
- Universal shift register modes
- Ripple vs synchronous counter
- Carry output using reduction AND
- Modulo counter concept

---

## 6. UDP, Tasks, and Functions

### 6.1 What a UDP is

UDP means:

- `User-Defined Primitive`

The lecture says Verilog already has standard primitives like:

- `AND`
- `OR`
- `NOT`
- `NAND`

But UDP lets you define custom primitive behavior using a table.

### 6.2 UDP rules

From the slides:

1. UDP cannot instantiate other modules or primitives
2. UDPs are instantiated like gate primitives
3. UDP has exactly one output
4. UDP output can be `0`, `1`, or `x`
5. `z` is not supported as an output state in UDP
6. input terminals must be scalar
7. output terminal is scalar and appears first
8. sequential UDP output must be declared `reg`
9. UDP is declared outside modules
10. `inout` is not supported

Memory aid:

- `UDP = one output, table-driven, primitive-like`

### 6.3 UDP syntax

General syntax from the slides:

```verilog
primitive udp_name (output_name, input_names);
  output output_name;
  input input_names;
  reg output_name;        // sequential UDP only
  initial output_name = value; // optional for sequential UDP
  table
    // rows
  endtable
endprimitive
```

### 6.4 UDP symbol meanings in state tables

The lecture includes special table symbols.

Important ones:

- `0` -> logic 0
- `1` -> logic 1
- `x` -> unknown
- `?` -> don't care
- `-` -> no change
- `(ab)` -> transition from a to b

Edge-related examples:

- `(01)` -> positive edge
- `(10)` -> negative edge

### 6.5 Combinational UDP

In combinational UDP:

- output depends only on current inputs

State table form:

```verilog
<input1> <input2> ... <inputN> : <output>;
```

The lecture notes maximum supported inputs:

- `10`

### 6.6 4:1 mux UDP example

The slides model a 4:1 mux as a UDP.

Big idea:

- selection inputs determine which data input reaches the output
- table rows define behavior for every important pattern

Why this matters:

- it shows truth-table style modeling directly in Verilog

### 6.7 Sequential UDP

In sequential UDP:

- next output depends on current inputs and current state

State table form:

```verilog
<inputs> : <current_state> : <next_state>;
```

Lecture points:

- output must be `reg`
- `initial` can set starting state
- max inputs effectively reduced because current state also participates

### 6.8 Types of sequential UDP

The slides divide them into:

1. level-sensitive sequential UDP
2. edge-sensitive sequential UDP

### 6.9 Level-sensitive sequential UDP example: latch

The lecture explains a latch UDP roughly as:

- if `reset = 1`, output `q = 0`
- if `reset = 0` and `clock = 1`, output follows `d`
- if `clock = 0`, output keeps previous state

This is exactly latch behavior:

- transparent when enabled
- holds value when not enabled

### 6.10 Edge-sensitive sequential UDP example: negative-edge D flip-flop

The lecture explains:

- if `reset = 1`, output is 0
- if `reset = 0`, data is captured on negative clock edge
- on positive edge or uncertain transitions, output may hold

This teaches how edge events can be encoded in UDP tables.

### 6.11 Functions vs tasks: high-level difference

The slides summarize this very clearly.

Function:

- called inside an expression
- returns one value

Task:

- called as a procedural statement
- can return values through output/inout arguments

### 6.12 Comparison table

Important differences from the lecture:

- Task may have zero or more input/output/inout arguments
- Function must have at least one input and does not use output/inout in the usual lecture simplification
- Task may return multiple values through outputs/inouts
- Function returns a single value through its function name
- Task may contain timing control
- Function may not contain timing control like `#`, `@`, `wait`, `posedge`, `negedge`

Memory aid:

- `Function = fast, one value, expression use`
- `Task = flexible procedure, can have timing`

### 6.13 When to use tasks

The slides say use a task when the procedure:

- has delay or timing control
- has at least one output argument
- has no input argument

Task syntax:

```verilog
task task_name(input ..., inout ..., output ...);
  // body
endtask
```

### 6.14 Task example idea

The lecture shows a `compare` task.

Concept:

- compare two numbers
- print whether `a > b`, `a < b`, or `a = b`
- possibly set a completion output

Why this is a task and not a function:

- it may produce side effects like `$display`
- it may return additional outputs

### 6.15 Another task example: temperature conversion

The slides also show a simple conversion task and a version using global variables.

Lesson point:

- tasks can be reusable local procedures
- but using explicit arguments is usually clearer than relying on globals

### 6.16 Calling task from another file/module

The lesson includes a separate-file calling example to show modular reuse.

Exam takeaway:

- tasks help prevent repeated code

### 6.17 When to use functions

Use a function when the procedure:

- computes one return value
- has no timing control
- is naturally used inside an expression

Function syntax:

```verilog
function return_type function_name(input ...);
  // body
endfunction
```

### 6.18 Function example

The lecture shows a `compare`-style function and a zero-count function example.

A function is ideal for something like:

- counting zeros
- computing parity
- selecting a result based on input value

because:

- it behaves like a combinational computation
- returns one result immediately in the same time unit

### 6.19 Practical exam rules for tasks and functions

If you see:

- `#10`, `@`, `wait`, or edge controls -> use `task`, not `function`
- one reusable computed return value -> `function`
- multiple outputs -> usually `task`
- called inside an expression -> `function`

### Most Likely to Appear in the Exam: UDP, Tasks, and Functions

- UDP definition and rules
- Difference between combinational and sequential UDP
- UDP table syntax
- Meaning of symbols like `?`, `-`, `(01)`, `(10)`
- Difference between task and function
- Why functions cannot have timing control
- When to use task vs function

---

# Quick Memory Sheet

## Arduino Fast Recall

- `setup()` runs once
- `loop()` runs forever
- `pinMode` configures pin direction
- `digitalWrite` outputs `HIGH/LOW`
- `digitalRead` reads digital state
- `analogRead` reads analog value
- `analogWrite` uses PWM, not true analog
- resistor protects LED
- pull-up prevents floating input
- PWM controls LED brightness and DC motor speed
- H-Bridge reverses DC motor direction
- servo uses pulse width
- EEPROM keeps data after power off

## HDL Fast Recall

- `initial` = once
- `always` = repeats
- combinational logic -> blocking `=`
- sequential logic -> nonblocking `<=`
- incomplete combinational assignment -> inferred latch
- decoder activates one output
- encoder converts active input to binary code
- mux selects one input
- demux routes one input to one output
- register stores data on clock edge
- async reset acts immediately
- sync reset acts on clock edge
- ripple counter is asynchronous
- function returns one value, no timing
- task can use timing and multiple outputs

---

# Final Night-Before-Exam Advice

If you are very short on time, focus on these in order:

1. Arduino commands, PWM, buttons, analogRead, RGB LED
2. DC motor vs servo vs stepper
3. EEPROM functions
4. Blocking vs nonblocking assignments
5. Decoder, encoder, mux, demux, comparator
6. D flip-flops, registers, shift registers, counters
7. UDP basics
8. Task vs function

Best active recall questions:

1. Why is `analogWrite()` called analog if Arduino is digital?
2. What is the difference between DC motor speed control and direction control?
3. Why is a pull-up resistor important?
4. When should you use `<=` instead of `=` in Verilog?
5. What causes an inferred latch?
6. What does a 4-to-1 mux really do?
7. Difference between asynchronous and synchronous reset?
8. Why can a function not contain `#10`?

---

# Source Extraction Note

The source PDFs were extracted locally, including OCR for scanned slide pages. Some image-heavy slides in the original PDFs contained diagrams and screenshots rather than clean embedded text, so this reviewer reconstructs and explains those visual lessons in plain language for study use.
