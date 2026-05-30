# 05: Register-Level LED Blinking {#led_blink}

Documenting the initial implementation of manual bitmask toggling on the development board without relying on high-level automated vendor tools.

## Core Reference Documentation Consulted
1. *i.MX RT1060 Processor Reference Manual (IMXRT1060RM)* - Chapter 13: Clock Controller Module (CCM), Chapter 26: IOMUX Controller (IOMUXC), Chapter 32: GPIO Blocks.

## Key Hardware Setup Struggles & Implementations

### 1. Pin Routing Configuration
The user LED on the board hooks into pin `GPIO_AD_B0_09`. To bridge this pin back internally to functional GPIO operations:
- Locate the IOMUX register block `IOMUXC_SW_MUX_CTL_PAD_GPIO_AD_B0_09`.
- Shift the function selector code down to write mode values (`ALT5`) into register bounds to isolate peripheral control.

### 2. Overcoming Clock-Gating Issues
By default, the peripheral clock gates are disabled to reduce system power footprint. To fix this:
- Configure `CCM_CCGR1` to open access boundaries to the `IOMUXC` module.
- Set bits across `CCM_CCGR2` to enable clocks for the physical `GPIO1` register block instance.

## Verified Implementation Reference File
- Review the low-level layout details directly inside the functional source implementation: @ref GpioDriver