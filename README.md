# EEE3088F-Micromouse


Josh:
- Battery monitoring with INA219 on I2C → Easy (DONE)
- Integrate USB-C and get 9V from USB Host → Medium
- Charge the battery from the 9V input → Hard
- ON/OFF switch with <30uA draw in OFF state → Hard

Kiyuran:
- 2x External Load Switching (1A High Side, 5V) → Easy
- Operate up to 4 motors bidirectionally → Medium
- 3V3 (300mA) & 5V (1.5A) power regulation → Medium
- Two charging modes (200mA & ~600mA ±100mA) → Hard



J: Battery monitoring with INA219 on I2C → Easy
INA219 is straightforward to integrate, with clear documentation and libraries.
The main challenge is setting A0/A1 correctly and ensuring accurate readings.

K: 2x External Load Switching (1A High Side, 5V) → Easy
Can be done using high-side MOSFETs (e.g., P-channel MOSFET or load switch IC).
Simple control logic and low power loss if chosen correctly.



K: Operate up to 4 motors bidirectionally → Medium
Requires an H-bridge motor driver (e.g., DRV8833, TB6612FNG) and PWM control.
Managing 4 motors while ensuring efficient power use is tricky but manageable.


J: Integrate USB-C and get 9V from USB Host → Medium
Requires a USB-C PD negotiation chip (e.g., STUSB4500, FUSB302) or resistors for fixed voltage.
Can be simplified using a prebuilt module but still involves some complexity.


K: 3V3 (300mA) & 5V (1.5A) power regulation → Medium
Requires LDOs or buck converters to ensure stable voltage with 5% accuracy.
Switching regulators (e.g., MP2315 for 5V, AMS1117 for 3.3V) improve efficiency.




J: ON/OFF switch with <30uA draw in OFF state → Hard
Needs an ultra-low-power power gating circuit (MOSFETs or dedicated power management IC).
Achieving <30uA standby current is tricky and requires careful component selection.

K: Two charging modes (200mA & ~600mA ±100mA) → Hard
Needs a method to switch charging currents, possibly using MOSFETs or a charge controller.
Requires careful current regulation to avoid damaging the battery.

J: Charge the battery from the 9V input → Hard
Requires a battery charging IC that can handle 9V input and safely regulate charging.
Heat dissipation and efficiency are concerns.










ERRATA:

v0.0 (Josh):
-Added INA219 circuit.
-Connected all inputs and outputs to the 32-pin header
-Used a shunt resistor to measure current using the INA219
-Connected A0 to ground and A1 to 3V3 (yields an address of 0x42)
END


