# Balloon Shooting Game
### Assembly Language Project — Department of Computer Science

---

## Overview

A real-time, interactive arcade-style game built entirely in x86 Assembly Language (8086)
targeting real-mode DOS. The player moves a character up and down on the left side of the
screen and shoots arrows at balloons floating from right to left. Miss 9 balloons and it's
Game Over.

This project demonstrates low-level programming concepts including:
- Direct video memory manipulation (segment 0B800h)
- BIOS/DOS interrupt-driven input and output
- Real-time game loop design
- Collision detection at the register level
- Score tracking with in-place screen updates

---

## Team Members

| Name       | Student ID | Responsibilities                  |
|------------|------------|-----------------------------------|
| Nahah Butt  | 23-UON-0338      | Game Logic, Collision Detection   |
| Muhammad Talha   | 23-UON-0446    | UI Rendering, Score System        |

---

## Controls

| Key         | Action                  |
|-------------|-------------------------|
| Up Arrow    | Move player up          |
| Down Arrow  | Move player down        |
| Spacebar    | Shoot arrow             |
| Enter       | Start / Restart game    |

---

## Technical Details

| Component     | Detail                              |
|---------------|-------------------------------------|
| Processor     | Intel 8086 / x86 (16-bit Real Mode) |
| Memory Model  | .model Small                        |
| Assembler     | MASM (Microsoft Macro Assembler)    |
| Platform      | MS-DOS / DOSBox                     |
| Video Memory  | 0B800h — CGA Color Text Mode        |
| Screen Mode   | Text Mode 3 (80x25, 16 colors)      |
| Keyboard      | BIOS INT 16h                        |
| Output        | DOS INT 21h + INT 10h               |

---

## How to Run

Requirements:
- DOSBox installed on your machine
- MASM (Microsoft Macro Assembler)

Steps:
1. Mount your MASM directory in DOSBox:   MOUNT C C:\MASM
2. Assemble the source file:              ML bubleshootinggame.asm
3. Run the game:                          bubleshootinggame.exe

Press Enter on the main menu to start playing!

---

## Project Structure

balloon-shooting-game/
│
├── bubleshootinggame.asm        -- Main game source code (Assembly)
├── README.md                    -- Project documentation
└── docs/
    └── Balloon_Shooting_Game_Report.docx  -- Full project report

---

## How It Works

Game Loop:
1. Check BIOS keyboard buffer for input
2. Handle keys (move player / fire arrow)
3. Check miss count — Game Over if 9 or more
4. Check collision (arrow_pos == loon_pos) — Hit!
5. Move balloon left by 160 bytes (one screen row)
6. Move arrow right by 4 bytes
7. Render all sprites to video memory
8. Repeat

Collision Detection:
Collision is detected by comparing the 16-bit video memory offsets of the arrow and the
balloon. When arrow_pos equals loon_pos, a beep sounds, the hit counter increments, and
a new balloon spawns.

---

## References

- Irvine, K. R. Assembly Language for x86 Processors (7th ed.), Pearson, 2014
- Intel 8086 Family Users Manual, Intel Corporation, 1979
- Ralf Brown's Interrupt List — http://www.ctyme.com/rbrown.htm
- DOSBox Project — https://www.dosbox.com

---

## License

This project was developed for academic purposes as part of the Assembly Language
course at the Department of Computer Science.
