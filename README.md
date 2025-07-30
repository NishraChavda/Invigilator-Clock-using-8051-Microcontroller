# Invigilator-Clock-8051 (C Language Version)

## Overview

This project implements an **Invigilator Clock** using an **8051 microcontroller**, programmed in **C language**. It functions as a countdown timer, suitable for examination environments to effectively display the remaining time.

## Features

- **Countdown Timer** from `02:59:59` to `00:00:00`
- **Multiplexed 7-Segment Display** for hours, minutes, and seconds
- **Auto Stop** when countdown reaches `00:00:00`
- **Efficient Refresh Mechanism** using a software delay and segment multiplexing

## Hardware Components Used

- AT89C51 / 8051 Microcontroller
- 6 x Common Cathode 7-Segment Displays
- Resistors for current limiting
- Crystal Oscillator (11.0592 MHz)
- Capacitors (typically 33pF) for oscillator
- Power Supply (5V regulated)

## Code Logic

### Initialization
- Countdown starts from `02:59:59`
- Digits stored in array `digits[] = {secU, secT, minU, minT, hrU, hrT}`

### Main Loop
- Continuously calls `show()` to refresh the display
- Uses `second_counter` to approximate a 1-second delay
- Calls `countdown()` every second to decrement time
- Countdown halts at `00:00:00`

### Display
- Port `P1`: Sends data to 7-segment segments
- Port `P2.0` to `P2.5`: Used to enable individual digits
- Uses time-division multiplexing to refresh digits one-by-one

## Applications

- Examination Timers
- Countdown displays for academic or personal use
- Embedded system time display projects

## Future Scope

- Add real-time clock (RTC) integration for accurate timing
- Add buttons to set custom start time
- Display control using IR remote or serial interface


