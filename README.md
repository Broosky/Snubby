# 💡 Snubby

Snubby is a subsystem of [Patchworks](https://github.com/Broosky/Patchworks) that I designed and built to detect overvoltage conditions on supply rails using independent, fully discrete comparator circuits.

The circuit operates in either latching (with hysteresis) or non-latching mode. Red and green LEDs indicate fault status, and a buffered output can drive a load or interface with an MCU or other circuitry.

In my implementation, the output connects to the power-on relay control node, allowing the system to automatically disconnect power if an overvoltage condition is detected. I intentionally added a latching feature so transient events are captured, making it easy to see if a fault occurred while I was away. Ultimately though, When triggered, the circuit disengages the power-on latch and shuts the board down.

Capacitive decoupling and filtering is handled in the main Patchworks project and this circuit is abbreviated as Snubby within it.

> If you found this project useful, interesting, or worth keeping an eye on, consider giving it a ⭐️.
> It helps others discover the project and motivates me to keep building and sharing more.

## 🔹 Construction

![Snubby 1](<Construction/Snubby 1.jpg>)

![Snubby 2](<Construction/Snubby 2.jpg>)

## 🔹 Rev A 1.1 Schematic

![Rev A 1.1](<Schematics/Rev A/Rev A 1.1.png>)

## 🔹 Rev A 1.1

- Increased Zener diode thresholds.
  - VCC input triggers at ~12.7 V.
  - 5 V rail triggers at ~5.8 V.
  - 3.3 V rail triggers at ~4.0 V.
- Swapped positions of red LED's and their respective limiting resistors.

## 🔹 Rev A 1

- Initial release.
- VCC input triggers at ~12.7 V (12 V + Q1 BE bias).
- 5 V rail triggers at ~5.4 V (4.7V + Q5 BE bias).
- 3.3 V rail triggers at ~3.7 V (3 V + Q9 BE bias).
- Hysteresis provided by R6, R16, and R25.
  - Remove these (and the pull-up transistor), or tie them to ground, for non-latching operation.

## 🔹 Rev B 1 Schematic

![Rev B 1](<Schematics/Rev B/Rev B 1.png>)

## 🔹 Rev B 1

- Initial release.
- Combined comparator outputs into a single detection stage.
- Non-latching operation.
- VCC input triggers at ~12.7 V.
- 5 V rail triggers at ~5.8 V.
- 3.3 V rail triggers at ~4.0 V.

##

> Educational Use Notice: This project is provided for educational and learning purposes only. You are welcome to read, study, and experiment
> with this software and/or hardware. It is not intended for commercial use. This software and/or hardware is provided "as is", without warranty
> of any kind. The author assumes no responsibility for any damages or issues resulting from its use.