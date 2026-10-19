# 3-DOF CNC Image Plotter

A three-axis Cartesian drawing robot designed to convert digital images into physical drawings on paper using CNC motion control.

![3-DOF CNC Image Plotter - 3D CAD Model](images/cnc-plotter-isometric.png)

## Table of Contents

- [Overview](#overview)
- [Objectives](#objectives)
- [Features](#features)
- [System Specifications](#system-specifications)
- [Working Principle](#working-principle)
- [Hardware and Materials](#hardware-and-materials)
- [Mechanical Assembly](#mechanical-assembly)
- [Electronics and Control](#electronics-and-control)
- [Software Requirements](#software-requirements)
- [Operating Procedure](#operating-procedure)
- [Applications](#applications)
- [Project Structure](#project-structure)
- [Limitations and Future Improvements](#limitations-and-future-improvements)
- [Team Members](#team-members)

## Overview

The 3-DOF CNC Image Plotter is a Cartesian robotic manipulator developed as a college mini project. It moves a drawing tool along three perpendicular axes to reproduce digital images and patterns on a flat surface.

The machine combines a mechanical frame, linear guide rods, lead screws, stepper motors, and an Arduino-based CNC controller. Image processing and G-code generation are performed using Inkscape, while Universal G-code Sender (UGS) is used to send motion commands to the controller.

The project demonstrates the practical integration of mechanical design, computer-aided manufacturing, motion control, and robotics.

## Objectives

- Design a three-degree-of-freedom Cartesian drawing robot.
- Develop controlled X-, Y-, and Z-axis movement.
- Convert digital images into machine-readable G-code.
- Draw images and geometric patterns on paper.
- Explore the use of CNC motion systems for engineering drawing and PCB-related applications.

## Features

- Three linear axes for positioning the drawing tool.
- Rectangular Cartesian mechanical configuration.
- Lead-screw-driven motion.
- Stepper-motor-based positioning.
- Image-to-G-code conversion workflow.
- Arduino and CNC Shield control architecture.
- Pen holder for drawing on paper.
- CAD-based mechanical design and 3D assembly visualization.

## System Specifications

| Parameter | Specification |
|---|---|
| Robot configuration | Cartesian |
| Degrees of freedom | 3 |
| X-axis workspace | 300 mm |
| Y-axis workspace | 400 mm |
| Z-axis travel | 60 mm |
| X-axis link dimension | 400 mm |
| Y-axis link dimension | 600 mm |
| Z-axis link dimension | 170 mm |
| Linear guide rods | 8 mm diameter steel rods |
| Drive mechanism | T8 lead screws |
| Stepper motors | 2 × NEMA 17, 1 × NEMA 23 |
| Controller | Arduino with CNC Shield |
| Drawing tool | Pen holder |
| Intended work surface | A4 paper |

**Note:** Workspace dimensions and structural link dimensions are different measurements. Actual usable travel depends on the final assembly, carriage dimensions, and end-stop positions.

## Working Principle

The machine follows a four-stage image plotting workflow.

### Stage 1: Image Preparation

An input image is opened in Inkscape. Its brightness, threshold, and image-processing settings are adjusted to obtain a suitable drawing representation.

### Stage 2: G-code Generation

The processed image or its converted drawing paths are exported to G-code using an appropriate Inkscape extension or conversion workflow.

G-code contains motion commands that specify tool movement, coordinates, feed rates, and pen or tool control where supported.

### Stage 3: Sending G-code

Universal G-code Sender (UGS) connects to the CNC controller over a serial connection and sends the commands for execution.

### Stage 4: Drawing

The controller drives the stepper motors to move the machine along the X, Y, and Z axes. The Z-axis raises or lowers the pen, while the X and Y axes trace the drawing paths.

The result is a physical reproduction of the processed image on paper.

## Hardware and Materials

The following materials and components are based on the original mini-project design.

### Mechanical Components

| Component | Material / Specification | Quantity |
|---|---|---:|
| Base plate | MDF or plywood, 18–20 mm | 1 |
| Gantry supports | MDF or mild-steel L-angle | 2 |
| Y-axis linear rods | Hardened steel, Ø8 mm | 2 |
| X-axis linear rods | Steel, Ø8 mm | 2 |
| Z-axis linear rods | Steel, Ø8 mm | 2 |
| Lead screws | T8 threaded rods | 3 |
| Anti-backlash nuts | Brass or Delrin | 3 |
| Linear bearings | Compatible with guide rods | Set |
| Flexible shaft couplers | Compatible with motor and lead screw shafts | Set |
| Z-axis plate | Wood, approximately 6 mm | 1 |
| Carriage plates and mounts | Aluminium or 3D-printed parts | Set |
| Pen holder | Spring-loaded or DIY design | 1 |
| Fasteners | Bolts, nuts, washers and mounting screws | As required |

### Electrical Components

| Component | Specification | Quantity |
|---|---|---:|
| X/Y stepper motors | NEMA 17 | 2 |
| Z-axis stepper motor | NEMA 23 | 1 |
| Stepper drivers | DRV8825 and/or TB6600, as compatible with the motors | As required |
| Controller | Arduino with CNC Shield | 1 |
| Power supply | 24 V DC, proposed 25 A / 600 W | 1 |
| Spindle motor | 775 motor, 24 V, 300 W | 1 for proposed milling configuration |
| Buck converter | 24 V to 5 V | 1, if required |
| Wiring and connectors | Suitable current-rated wiring and terminals | Set |
| Emergency stop and power switch | Suitable ratings | As required |
| Limit switches | Compatible with the controller | Recommended |

**Important:** The spindle motor is associated with the proposed milling configuration. The demonstrated paper-drawing application uses a pen holder. Do not assume the spindle is required for ordinary pen plotting.

The original design specifies a 24 V, 25 A power supply. Verify the actual motor and driver ratings, spindle requirements, and wiring before purchasing or powering the system. Stepper motor rated phase current is not the same as the DC supply current, so the power supply must be sized using the actual driver and load specifications.

## Mechanical Assembly

The following is a recommended assembly sequence for the Cartesian structure. Confirm the mounting-hole positions, rod spacing, and part dimensions against the supplied CAD files before fabrication.

### Step 1: Prepare the Base

- Cut the MDF or plywood base to the dimensions of the mechanical design.
- Mark the mounting positions for the gantry supports and Y-axis guide rods.
- Drill the required mounting holes.
- Check that the base is flat and stable.

### Step 2: Install the Gantry Supports

- Attach the two gantry supports to the base.
- Keep the supports parallel and perpendicular to the intended axis of travel.
- Check that the supports are firmly fixed and do not wobble.

### Step 3: Assemble the Y-Axis

- Mount the two Y-axis linear guide rods.
- Install the corresponding bearing blocks or carriage supports.
- Fit the Y-axis lead screw and its nut.
- Couple the lead screw to the appropriate stepper motor.
- Move the carriage manually, with the motor disengaged as appropriate, to check for binding.

### Step 4: Assemble the X-Axis Gantry

- Mount the X-axis guide rods and lead screw onto the moving gantry or cross-axis structure.
- Install the X-axis carriage and bearing blocks.
- Attach the X-axis stepper motor and lead-screw coupler.
- Check the alignment and full travel of the carriage.

### Step 5: Assemble the Z-Axis

- Attach the Z-axis plate and guide rods to the X-axis carriage.
- Install the Z-axis lead screw, nut, and stepper motor.
- Ensure that the Z-axis moves smoothly in both directions.
- Check that the tool can reach the paper without colliding with the base.

### Step 6: Install the Pen Holder

- Attach the pen holder to the Z-axis carriage.
- Align the pen tip vertically with the drawing surface.
- Adjust the pen height and, if fitted, the spring pressure.
- Confirm that the pen lifts sufficiently during non-drawing movements.

### Step 7: Check Alignment and Travel

- Move each axis through its intended travel range.
- Check for binding, loose fasteners, lead-screw misalignment, and collisions.
- Verify the usable X-, Y-, and Z-axis workspace.
- Install and test end stops or limit switches where supported.

## Electronics and Control

The proposed control architecture consists of an Arduino-based controller, CNC Shield, stepper drivers, stepper motors, and a DC power supply.

### Basic Connection Architecture

1. Connect the Arduino and CNC Shield according to the board manufacturer's pinout.
2. Install compatible stepper drivers for each motor.
3. Connect the X-, Y-, and Z-axis stepper motors to their respective driver outputs.
4. Connect the limit switches to the supported input pins, if installed.
5. Connect the motor power supply to the appropriate CNC Shield power input.
6. Provide a separate, correctly rated power arrangement for the spindle if the milling configuration is implemented.
7. Connect the controller to the computer through USB for G-code communication.

**Safety:** Disconnect power before wiring or changing drivers. Check driver current limits, motor coil pairs, supply polarity, grounding, and thermal requirements. Never power a spindle directly from an Arduino output. Provide appropriate emergency stopping and spindle isolation before operating a milling configuration.

The exact wiring depends on the selected Arduino, CNC Shield revision, stepper drivers, and firmware configuration. Refer to their datasheets and pinout documentation.

## Software Requirements

### 1. Inkscape

Used to prepare the input image and generate drawing paths or G-code through a compatible extension or conversion workflow.

### 2. Universal G-code Sender (UGS)

Used to establish serial communication with the CNC controller and send G-code commands.

### 3. Arduino Firmware

The controller requires compatible CNC firmware, such as a suitable GRBL configuration for the selected board. Confirm that the firmware supports the controller, installed drivers, and required axis configuration before operation.

### 4. Computer and USB Connection

A computer is used to prepare the drawing, connect to the controller, configure the machine, and monitor G-code execution.

## Operating Procedure

1. Inspect the mechanical assembly and check that all fasteners are secure.
2. Verify motor wiring, driver settings, power supply ratings, and limit-switch operation.
3. Connect the Arduino-based controller to the computer.
4. Open UGS and select the correct serial port and communication settings.
5. Confirm that the firmware responds correctly.
6. Home the machine if homing switches and firmware support are configured.
7. Prepare the input image in Inkscape.
8. Generate G-code using a compatible conversion or export workflow.
9. Check the G-code, travel limits, drawing scale, and pen-lift commands.
10. Test the toolpath with the pen raised or by running a safe, controlled dry run.
11. Place and secure the paper on the work surface.
12. Set the drawing origin and pen height.
13. Send the G-code and monitor the machine throughout execution.
14. Stop the machine if unexpected movement, binding, or other unsafe behaviour occurs.

## Applications

- Drawing geometric patterns and technical sketches.
- Plotting logos, line drawings, and processed images.
- Reproducing simple artwork and text where supported by the conversion workflow.
- Demonstrating Cartesian robotics and CNC motion control.
- Educational experiments involving G-code and stepper motors.
- Exploring PCB milling as a future extension after suitable hardware and safety upgrades.

## Project Structure

Organize the repository so that CAD files, images, and documentation are easy to find.

```text
3DOF-CNC-Image-Plotter/
├── README.md
├── images/
│   ├── cnc-plotter-isometric.png
│   ├── front-view.png
│   ├── side-view.png
│   ├── top-view.png
│   ├── assembly-view.png
│   └── plotted-results.png
├── cad/
│   ├── native-model-files/
│   ├── exported-model-files/
│   └── drawings/
├── electronics/
│   ├── wiring-diagram.png
│   └── component-notes.md
├── software/
│   ├── firmware/
│   └── sample-gcode/
└── docs/
    ├── mini-project-report.pdf
    └── assembly-notes.md
```

This is a suggested structure. Keep only folders and files that you actually upload. Place the original CAD project files in `cad/`, exported models in `cad/exported-model-files/`, and the final report in `docs/`.

## Limitations and Future Improvements

- Improve the rigidity of the base and gantry to reduce vibration.
- Improve lead-screw alignment and backlash compensation.
- Add or refine homing switches and travel-limit protection.
- Improve pen lifting and pressure control for more consistent drawings.
- Calibrate axis travel and drawing scale.
- Add a documented wiring diagram and tested firmware configuration.
- Explore PCB milling only after validating spindle mounting, tool runout, workholding, motion accuracy, electrical isolation, and dust/chip protection.

## Team Members

- **Aswin S Pillai** — Roll No. 12
- **Ajith Unnikrishnan** — Roll No. 37
- **Avinue Krishna** — Roll No. 13
- **Adwaith Prasannakumar** — Roll No. 04

## Project Status

The project demonstrated a three-axis Cartesian CNC plotter capable of drawing an input image on A4 paper. The repository contains the available design files, assembly views, and project documentation.

**Note:** The exact CAD files, wiring, firmware, and software workflow included in this repository should be treated as the authoritative implementation details. Any proposed components or future features should be clearly distinguished from the hardware actually assembled and tested.
