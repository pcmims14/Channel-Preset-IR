Q-SYS Channel Preset Keypad Sequencer

This Q-SYS Lua script allows preset buttons to automatically dial TV channels by simulating numeric keypad presses with a configurable delay and an ENTER command sent after the final digit.

How It Works

Each preset button corresponds to a channel number stored as a string (e.g. 901).

The string is parsed into individual digits.

Digits are sent sequentially using Controls.numbers[n]:Trigger().

A user-defined delay is applied between each keypress.

ENTER is triggered one delay after the final digit.

Features

Radio-style (interlocked) preset buttons

Sequential keypad triggering with precise timing

Millisecond-based delay control

Correct handling of digit 0 (mapped to keypad index 10)

ENTER key sent as a final, delayed step

Safe, named global timer compliant with Q-SYS scripting rules

Clean restart behavior when changing presets mid-sequence

Required Controls

Your Q-SYS design must include the following control arrays:

Controls.presetButtons[] — Toggle buttons for channel presets

Controls.definedChannelNumbers[] — String controls containing channel numbers

Controls.numbers[] — Trigger controls for keypad digits

Index 1–9 = digits 1–9

Index 10 = digit 0

Controls.Enter — Trigger control for the ENTER key

Controls.delayCommandTime — Numeric control (milliseconds)

Timing Notes

Delay values are entered in milliseconds

Internally converted to seconds for Timer:Start()

Typical values: 100–250 ms

Q-SYS Timer Requirements

This script follows Q-SYS timer rules:

Timer is global

Timer is named

Only one timer is used per control script

Do not convert the timer to a local variable.

Example

Preset channel string:

901


Triggered sequence:

9 → 0 → 1 → ENTER

Intended Use

Designed for TVs, set-top boxes, and displays that require keypad-style channel entry via control triggers.
