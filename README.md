# Packaging Line Control System (PLC-Based)

## Overview

This project implements a PLC-based automation system for a packaging line that fills boxes with apples. The system controls conveyors and uses sensors with a counter to ensure each box contains exactly 10 apples.

## System Components

**Inputs**

* I0.0 — Start push button (NO)
* I0.1 — Stop push button (NC)
* I0.2 — Apple detection sensor
* I0.3 — Box presence sensor

**Outputs**

* Q0.0 — Box conveyor
* Q0.1 — Apple conveyor

**Internal Memory**

* M0.0 — Run latch

**Counter**

* C0 — Up counter (Preset = 10)

## Operation

* Pressing START (I0.0) latches the system in RUN mode.
* Pressing STOP (I0.1) stops all operations.
* The box conveyor runs until a box is detected by I0.3.
* When a box is present, the box conveyor stops and the apple conveyor starts.
* Apples are counted via I0.2 using counter C0.
* When the count reaches 10, the apple conveyor stops, the counter resets, and the box conveyor restarts.
* The cycle repeats automatically.

## PLC Logic Structure

* Network 1: Start/Stop latch
* Network 2: Box conveyor control
* Network 3: Apple conveyor control
* Network 4: Counter logic

## Tools

* Siemens STEP 7 / TIA Portal
* S7-PLCSIM

## Note

In practical implementation, a rising edge (one-shot) detection should be used on the apple sensor to ensure accurate counting.

## Author

Ayesha Sadia
