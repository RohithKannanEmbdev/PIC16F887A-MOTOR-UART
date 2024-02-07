# PIC16F887A-MOTOR-UART

This PIC microcontroller code appears to control two output pins (RD0 and RD1) based on the received commands via UART. 
The commands are 'R', 'L', and 'S', and each command corresponds to a specific action on the pins

Initialization:
The TRISD register is set to configure RD0 and RD1 as output pins.
The TRISC register is configured for UART communication.
ANSEL and ANSELH are set to 0 to configure all analog pins as digital.

UART Configuration:
TXSTA is set to 0x24, configuring the UART for transmission (TXEN bit) and asynchronous mode (SYNC = 0).
RCSTA is set to 0x90, enabling the serial port (SPEN bit) and reception (CREN bit).
SPBRG is set to 25, configuring the baud rate.

Main Loop:
The main loop continuously prompts the user to "Enter Position" via UART using the transmitString function.
It then waits to receive a character using the receiver function, storing the received character in positionCommand.
Based on the received command, the code performs the following actions:
If positionCommand is 'R', RD0 is set to 0, and RD1 is set to 1.
If positionCommand is 'L', RD0 is set to 1, and RD1 is set to 0.
If positionCommand is 'S', both RD0 and RD1 are set to 0.


This code essentially allows the microcontroller to control the state of two output pins (RD0 and RD1) based on the commands received via UART.
The commands 'R', 'L', and 'S' are used to indicate right, left, and stop actions, respectively. 
The actual hardware or system being controlled by these pins would need to interpret these signals accordingly.
