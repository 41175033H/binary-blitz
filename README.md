# Binary Blitz — FPGA Mini-Game

Match the displayed decimal number in **binary** on the switches before the **buzzer** sounds. Built for Digital Lab final project.

## Hardware & Tools
- **Board:** DE10-Lite (Intel MAX 10 10M50DAF484C7G)
- **Language:** Verilog
- **Toolchain:** Quartus Prime 19.1 (Lite)
- **Clock:** 50 MHz (`CLOCK_50`)
- **Peripherals:** 6× seven-segment HEX displays, 10× switches, 2× push-buttons, LEDR[9:0], GPIO buzzer

## How to Play
1. Press **Start** （Key see in pin map) to begin a round.  
2. A random target number 0–15 appears on 7-segment.  
3. Set the **binary value** on SW3-SW0
4. Correct before the timer expires → win tone; otherwise → buzz.

## Build & Flash (Quartus)
1. Open the project (`timer.qpf`).
2. Ensure constraints are present:
   - **Pins:** `constraints/timer.qsf` (from this repo)
   - **Timing:** `constraints/binary_blitz.sdc` (see snippet below)
3. **Compile**.
4. **Program Device** via USB-Blaster.

## Design
![Block Diagram](docs/block-diagram.png)

## Pin Map (timer.qsf)
| Signal | Pin | Notes |
|-------|-----|------|
| CLK_50 | N5 | 50 MHz |
| PB     | B8/A7 | start-submit/reset |
| SW[3:0] | C10, C11, D12, C12 | binary input |
| SEG_A[7:0] | B20, A20, B19, A21, B21, C22, B22, A19 | HEX0 |
| SEG_B[7:0] | F21, E22, E21, C19, C20, D19, E17, D22 | HEX1 |
| SEG5[6:0] | J20, K20, L18, N18, M20, N19, N20 | HEX5 |
| BUZZER | W10 | GPIO |

## Demo
- Full video: [link](https://www.youtube.com/watch?v=8COTSkyvL00)
- 30-sec video: [link](https://www.youtube.com/watch?v=DdROMYIEj-0)
- Screenshot/GIF: `media/demo.gif`

## Authors
吳炳煌, 張慎修，MIT License.
