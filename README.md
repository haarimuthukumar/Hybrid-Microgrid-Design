# Hybrid-Microgrid-Design

Author: Haari Muthukumar
Description: A 4.16kV Hybrid small residential microgrid, with a 2MVA Photovoltaic Solar system, 1.5MVA Battery Energy Storage System, and IEEE standard protective equipment. 

# Project Overview
As someone interested in solar energy and sustainability, I was curious to see how this impacted our everyday communities and the power that we get. I have created a single-line diagram model and am currently modeling the power flow in Python to get a grasp of the concepts of grid protection and grid integration with renewable energy and battery storage systems for a self-sustaining microgrid.

# Singe Line Diagram
Look at the `SingleLineDiagramMicrogridModel.pdf` in the  repository for the electrical AutoCAD schematic

# Design Choices
For a more detailed explanation of choices, refer to Hybrid Microgrid Design and Safety Choices_Project overview.pdf

# Voltage Levels
*13.8kV Utility Tie*: Standard distribution voltage coming into a small neighborhood from the larger macrogrid.

*4.16kV Distribution Bus*: Stepped down from 13.8kV by a 2.5 MVA delta-wye transformer to travel through the neighborhood via busbar, reducing arc flash severity and equipment costs (circuit breakers and switchboxes at higher voltages take up more space and are more expensive)

*480V Generation Branches*: Solar PV and BESS operate at 480V (North American Standard). Because solar panels and batteries output DC voltage, inverters convert DC to AC before step-up transformers bump the voltage up to 4.16kV for the busbar. The BESS uses a bidirectional inverter to convert DC to AC when discharging and AC to DC when storing power.

*120/240V Residential Service*: The residential branch drops the 4.16kV to the 120/240V residential voltage using a one phase split transformer.

# Phase Allocation
*3-Phase System (Most of Grid/Busbar)*: Provides continuous power with a 120-degree phase shift, yielding ~73% more power while using less conductive material for efficient travel

*1-Phase System (Residential)*: Drops down to single-phase for residential loads, allowing for a safer low voltage with cheaper and smaller  equipment

# Safety & Protective Relaying Architecture

*Circuit Breakers*: Positioned before and after major components to shut down current during component or macrogrid failure to safely island or isolate the microgrid

# ANSI Device Functions:
*ANSI 50/51 (Instantaneous & Time-Delay Overcurrent)* : Short-circuit and overcurrent protection

*ANSI 27/59 (Under/Over Voltage) & ANSI 81 (Under/Over Frequency)*: Positioned near solar and BESS inverters to comply with IEEE standards (1547), preventing component damage from voltage or frequency variations.

*ANSI 25 (Synchronism Check)*: Put on the main utility line to make sure the neighborhood busbar voltages match utility voltages at the point of common coupling (PPC) before rejoining the macrogrid after islanding.

ANSI 67 (Directional Overcurrent)*: Checks directional differences between utility and microgrid sides, especially useful during faults, preventing power backflow

# PT & CT Placement:
PT/CT sets in the utility branch feed voltage/current data to the protective relay for ANSI device function; they are placed next to each other between inverters and the transformer to prevent distorted readings. PTs/CTs are also located between inverters and transformers on the BESS and Solar branches for sensing that can be used for  anti-islanding.

## Equipment Choices

The equipment table is in the`SingleLineDiagramMicrogridModel.pdf`in the repository.

All equipment adheres to the IEEE standards.

# Important Equipment 

*Delta-Wye Transformer:* Provides ground fault protection and fault isolation (ground faults on the Wye side cannot pass through Delta) using 3-wire primary runs.

*Split Phase Transformer:* Provides two voltage levels through the differing phase angles between the hot and neutral, and the top and bottom wires.
*Inverters:* Use a 3-phase grid-tied solar inverter and a 4-quadrant bi-directional BESS inverter to allow two-way power flow for battery charging and discharging.

# Standards
Uses IEEE Standards for this design but doesn't focus on controllers or testing

# Files:
## Repository Files
* `SingleLineDiagramMicrogridModel.pdf` — Single Line Diagram CAD schematic
* `Hybrid_Microgrid_Design_Rationale.pdf` — Design Report

 
