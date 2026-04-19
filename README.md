# network_checker_detector



A hardware-based **Sequential Network Cable Tester** designed in KiCad. This tool detects signal frequency and pin-to-pin continuity for RJ45 Ethernet cables.

##  Project Description
This device identifies wiring faults in network cables by cycling a signal through all 8 pins sequentially. It uses hardware logic (no MCU required) to provide real-time visual feedback via an LED array.

### Features
*   **Sequential Testing:** Automatically cycles through pins 1-8.
*   **Hardware Logic:** Uses a 555-Timer and 4017-Counter architecture.
*   **Visual Debugging:** 10-LED indicator row for signal tracking.
*   **Low Power:** Designed for standard DC input or 9V battery operation.

---

##  Hardware Architecture

### Logic Flow
1. **Clock Generation (U1):** An **NE555 Timer** generates a square wave (the system heartbeat).
2. **Signal Sequencing (U3):** A **CD4017 Decade Counter** receives the clock and shifts a "High" signal across pins 0-7.
3. **Transmission (J1/J3):** The signal is sent through the RJ45 connectors.
4. **Visual Output:** If the physical wire is intact, the corresponding LED (D2-D19) illuminates.

### Key Components

| Ref | Component | Description |
| :--- | :--- | :--- |
| **U1** | NE555 | Astable Multivibrator (Clock) |
| **U3** | CD4017 | Decade Counter (Sequencer) |
| **D2-D19** | 1N4148 | Signal Diodes (Backflow Protection) |
| **J1, J3** | RJ45 | Ethernet Testing Ports |

---

##  Repository Structure
```text
├── hardware/
│   ├── networkdetector.kicad_sch  
│   ├── networkdetector.kicad_pcb  
│   └── networkdetector.kicad_pro  
├── renders/
│   └── 3d_view.png               
└── docs/
    └── BOM.csv                    
