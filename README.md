<img width="1366" height="342" alt="BB_Banner_RMaDSD_ULTRA@300x(Medium)" src="https://github.com/user-attachments/assets/accb3f21-66a9-41ee-bdb2-473654d2ef2c" />

# I2C Target Firmware

A reference firmware to be flashed on the STM32F407 Discovery Board. This binary configures the board to be an I2C Target, with the address of `0x42`. When on the development board, the firmware is capable of recovering from common I2C errors to make testing of custom Controller firmware easier.

Flash the firmware using [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html), using the onboard ST-Link. Download the .bin file from this release.

## Connection Example

<img width="7355" height="5495" alt="I2C@8x" src="https://github.com/user-attachments/assets/9804e111-bb35-4537-9d73-94b4f8144b17" />

## Key Information
📌 Target Address: `0x42`
📌 I2C Pins: `PB6` for *Clock* `PB7` for *Data*
📌 User Button: Press to cycle between values `0`, `25`, `50`, `75`, `100`. Once reaching `100`, the button will reverse the direction.
📌 Reset Button: Resets the hardware.
📌 TX Data: When the button is pressed, the latest value is transmitted when requested by the Controller. Once that value is returned the firmware returns default data until the button is pressed again.
📌 Default data: The firmware transmits a value of `0xFF` if no new data is available when requested by the Controller.
📌 Blue LED: The blue LED illuminates during and for 100 ms after transmitting data to the Controller
📌 Green LED: The green LED illuminates relative to the value from the user button and remains illuminates at that level until the button is pressed, i.e., if the button is pressed and returns `75` the LED will be 75% illuminated.
📌 Probe Point: Pin PD12 can be tested with an Oscilloscope to see the current value being output to the green LED and transmitted by I2C. The pin is PWM'd at 10 kHz between 0-100% duty cycle.

> [!IMPORTANT]
> Please flash the firmware onto a board which does not have the expansion board with the serial interface, allow that board to be used by other members of the cohort who need the serial interface to output UART/USART to the PC.
