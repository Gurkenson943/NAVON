# NAVON Syntax

**File extension:** `.nvn`

## Comments

```navon
?{ Comment }
```

Creates a normal comment.

```navon
?[ Side comment ]
```

Creates a side comment.

```navon
?/ Multi-line
comment /
```

Creates a multi-line comment.

---

## Variables

```navon
set(x): 1;
```

Sets `x` to `1`.

```navon
set(x): y;
```

Sets `x` to the value of `y`.

```navon
set(x): "Hello";
```

Sets `x` to the string `"Hello"`.

```navon
change.global(x);
```

Makes `x` a global variable.

```navon
change(x): + 1;
```

Adds `1` to `x`.

```navon
change(x): - y;
```

Subtracts `y` from `x`.

### Operators

| Operator | Meaning        |
| -------- | -------------- |
| +        | Addition       |
| -        | Subtraction    |
| /        | Division       |
| *        | Multiplication |
| **       | Power          |

Example:

```navon
change(x): / 2;
```

Means:

```text
x = x / 2
```

```navon
change(x): y / 2;
```

Means:

```text
x = y / 2
```

---

## Lists / Sets

```navon
set.list(x): { 1, 2, 3 };
```

Creates a set containing 1, 2 and 3.

```navon
set.list(x): { 1, 2 ~ 4 };
```

Creates a set containing 1 and all values from 2 to 4.

### Modify Sets

```navon
change.list(x): + { 3, 4 };
```

Adds 3 and 4 to set `x`.

```navon
change.list(x): - { y };
```

Removes `y` from set `x`.

---

## Output

### Console

```navon
give.com(x);
```

Prints `x` to the console.

### Window

```navon
give.win(x);
```

Prints `x` inside a window.

```navon
give.win(x): + [
    place(10, 10);
    color(255,255,255);
    size(25)
];
```

Prints `x` at position `(10,10)` in white with size `25`.

### Expressions

```navon
give.com(x + y);
```

Prints the result of `x + y`.

```navon
give.com("x + y");
```

Prints the literal text:

```text
x + y
```

### Variable Replacement

```navon
give.com("x is equal to <x>");
```

Example output:

```text
x is equal to 5
```

---

## Functions

### Define Function

```navon
def(x):
```

Defines function `x`.

```navon
def(x): + (attribute);
```

Defines a function with an attribute.

### Parameters

```navon
def(x): [ add: x, y ]:
```

Defines a function that accepts parameters.

### Return Values

```navon
def(x): [ add: x, y ]:
    return(x + y);
stop;
```

Example:

```navon
set(z): [ function.x(2,3) ];
give.com(z);
```

Output:

```text
5
```

### Calling Functions

```navon
function.x
```

Calls function `x`.

### Global Functions

```navon
global.x;
```

Makes function `x` globally accessible.

---

## Program Entry Point

```navon
start.programm(
```

Code inside this block executes when the program starts.

Example:

```navon
def(name):
    change(x): + 1;
    give.com(x);
stop;

global.name;

start.programm(
    set(x): 1;
    function.name;
stop)
```

Output:

```text
2
```

---

## Imports

```navon
implement.random;
```

Imports a module.

### Available Modules

#### random

```navon
random.random(x): [ x, y, z ];
```

Chooses a random variable.

```navon
random.random(x): [ "x", "y", "z" ];
```

Chooses a random string.

```navon
random.Number(x);
```

Returns a random floating-point number.

```navon
random.Number(<x>);
```

Returns a random integer.

```navon
random.data(x): [ file1.txt, file2.txt ];
```

Chooses a random file.

```navon
random.r(x);
```

Defines a random value.

### Random Seed

```navon
random.seed(x);
```

Creates a random code consisting of digits 0–9 with `x` digits.

Example:

```navon
set(x): [ random.seed(3) ];
give.com(x);
```

Output:

```text
734
```

---

## JSON Module

### Save

```navon
json.save(x): [ file.json ];
```

Saves `x` to a JSON file.

### Load

```navon
json.load(file.json);
```

Loads data from a JSON file.

---

## Math Module

### Constants

```navon
math.pi
```

Pi.

```navon
math.e
```

Euler's number.

### Square Root

```navon
math.sqrt(x)
```

Square root of `x`.

Example:

```navon
set(x): 25;
change(x): [ math.sqrt(x) ];
give.com(x);
```

Output:

```text
5
```

---

## Data Module

```navon
implement.data;
```

### Data Visualization

```navon
depict.data(x): [ ... ];
```

Draws data using one of the following states:

```navon
state(table)
state(diagram-line)
state(diagram-cir)
state(diagram-bar)
state(diagram-heat)
state(graph)
```

### Data Definition

```navon
data(
```

Defines data for visualization.

### Select Columns

```navon
data.select(x): [ "z", "y", "x" ];
```

### Filter

```navon
data.filter(x): [ x > 1 ];
```

### Sort

```navon
data.sort(x): y;
```

### Data Sources

```navon
data.data(x): [ file.txt; file.nvn ];
```

### Average

```navon
set(x): [ avg(set) ];
```

Calculates the average value.

---

## Data Windows (dw)

```navon
make.dw(
    windows.title("Hello");
    windows.color(white);
    windows.size(zoomed);
stop)
```

Creates a Tkinter window.

---

## Conditions

### If

```navon
if(x): = 1;
```

Runs if `x == 1`.

### Else If

```navon
else-if(x): = 2;
```

Runs if previous condition failed and `x == 2`.

### Else

```navon
else;
```

Runs otherwise.

### Comparison Operators

| Operator | Meaning               |
| -------- | --------------------- |
| =        | Equal                 |
| >        | Greater than          |
| >=       | Greater than or equal |
| <        | Less than             |
| <=       | Less than or equal    |
| n=       | Not equal             |

---

## Loops

### While

```navon
while(x): = 2;
```

Runs while `x == 2`.

### For

```navon
for(x): [1 ~ 10];
    give.com(x);
stop;
```

Outputs:

```text
1
2
3
...
10
```

---

## Keyboard & Mouse Input

```navon
key.x
key.esc
key.space
key.up
key.mleft
key.mright
key.mroll
```

### Key Detection

```navon
if(key.x): = True;
```

Triggered when key is pressed.

```navon
if(key.x): = pressed;
```

Triggered while key is held down.

---

## Rounding

```navon
round(x);
```

Rounds to nearest integer.

```navon
round.on(x): = 3;
```

Rounds to 3 decimal places.

Example:

```navon
set(x): [ round.on(2.3456765): = 3 ];
give.com(x)
```

Output:

```text
2.346
```

---

## Syntax Rules

Every line must end with:

```navon
;
```

Except when the line ends with:

```navon
:
(
[
```

Blocks must end with:

```navon
stop
```

Example:

```navon
if(x): = 2;
    give.com("x is equal to 2");
else;
    give.com("x is equal to <x>");
stop
```

---

## Windows

### Create Window

```navon
make.windows(
```

### Properties

```navon
windows.title("Hello");
windows.color(white);
windows.size(x,y);
windows.size(zoomed);
windows.size(full);
```

### Close Window

```navon
close(windows);
```

---

## Graphics

### Draw Objects

```navon
depict(x): [
    state(rec);
    place(10,10);
    color(255,255,255);
    size(10,10)
];
```

### States

```navon
state(rec)
state(cir)
state(line)
state(button)
```

### Buttons

```navon
depict(start): [
    state(button);
    text("Start Program");
    text.co(black);
    place(10,10);
    color(white);
    size(50,50)
];
```

---

## Images, Sounds and Videos

```navon
load.image(file.png);
load.sound(file.mp3);
load.video(file.mp4);
```

### Create Assets

```navon
set.texture(x);
set.sound(x);
set.video(x);
```

Example:

```navon
set.texture(hero): [ load.image(hero.png) ];
depict(hero): [
    place(x,y);
    size(10,10);
    hero
];
```

---

## Boolean Operators

```navon
not
and
or
```

---

## Program Control

### Break

```navon
break;
```

Stops a function or the program.

### Return

```navon
return(x);
```

Returns a value.

---

## Colors

### Define Colors

```navon
set.color(black): [0,0,0];
```

```navon
set(x): 255;
set.color(white): [x,x,x];
```

Several colors are predefined.

---

## Collision

```navon
collision(x): = True;
```

Object has collision.

```navon
collision.only(x): [ y, z ];
```

Object collides only with `y` and `z`.

---

## Fill

```navon
fill(x): [ white ];
```

Fills object with a color.

---

## Clear

```navon
clear(x);
clear(text);
clear(all);
```

Removes drawings or text.

---

## User Input

```navon
give.com("What is your age?");
set(age): [ input ];
give.com("You are <age> years old");
```

Output:

```text
What is your age?
20
You are 20 years old
```

---

# Errors

### Error Handling

```navon
if(error): = True;
```

### Display Error

```navon
give.com(error);
```

Prevents the program from crashing.

### Standard Traceback

```text
Traceback (most recent call last):
  File "<file>", line x, in <module>
Error-type
```

### Error Types

#### Syntax-error

Missing indentation or missing semicolon.

#### Attribute-error

```text
(<attribute or method> is missing)
```

#### Overflow-error

Number too large.

#### Global-error

```text
(<x> is not global)
```

#### Type-error

```text
(<wrong word> did you mean <suggestion>)
```

#### Func-error

```text
(<name> is not defined)
```

#### Number-error

Invalid numeric value.

#### Index-error

Index outside list bounds.

#### File-error

File missing or unreadable.

#### Key-error

Dictionary key not found.

#### Calculation-error

```text
(<calculation> is not possible)
```

#### Division-by-0-error

Division by zero.

#### Intern-error

Internal NAVON error.

---

# NAVON REPL

When NAVON starts:

```text
Welcome to NAVON REPL. write:
help(true): to get help
credits(true): to see the credits
exit(true): to exit
```

```text
nvn>
```

You may enter NAVON code directly.

---

## Commands

### Help

```navon
help(true);
```

Shows syntax and command help.

### Exit

```navon
exit(true);
```

Output:

```text
You're exiting now NAVON. BYE BYE
```

### Credits

```text
=== NAVON CREDITS ===

Concept:
Paul Kaschnitz

Art:
Paul Kaschnitz

Code-Team:
Paul Kaschnitz

Made in Austria, Salzburg by Paul Kaschnitz ©

=== NAVON ===
```

---

## Running NAVON Files

```bash
navon file.nvn
```

Starts a NAVON script.

### Start NAVON

```bash
navon
```

### Installation

```bash
cd C:\navon
pip install -e .
```

Graphics support:

```bash
pip install -e ".[graphics]"
```

---

# Planned Improvements

## Fixes

1. Input handling in windows
2. Update system and screen flickering
3. Clear function
4. Button interaction
5. Texture loading
6. Collision system
7. Additional keyboard keys
8. Fill function
9. Random module completion
10. Boolean operators (and/or/not)
11. Error handling

## New Features

### Wait

```navon
wait(x);
```

Waits `x` seconds.

### Data Module

```navon
implement.data;
```

### Executable Builder

```navon
navon.exec[
    --add-data("hero.png;.");
    --set.icon("game.ico;.");
    --name("GAME");
    herogame.nvn
]
```

Builds a standalone `.exe` using PyInstaller with `--onefile`.

### Window Refresh

```navon
window.show(true);
```

Defines when the display updates.
