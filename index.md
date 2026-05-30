# Custom i.MX RT1060 Bare-Metal Wiki Index {#mainpage}

Welcome to my personal, register-level hardware exploration journal for the NXP i.MX RT1060 EVKC development kit. This contains full documentation tracking every software architectural milestone built entirely from scratch.

## Project Milestones & Engineering Diaries
1. @subpage getting_started "Getting started"

## Structural Development Environment Summary
- **Toolchain:** ARM GNU Toolchain (`arm-none-eabi`) cross-compiling via WSL2 inside a VS Code development loop.
- **Linker Configuration:** Explicit custom FlexRAM structural partition managing Flash execution (XIP).