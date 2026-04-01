# Access Control Controller Hardware Design

## Project Introduction

This project is a hardware design solution for an access control controller based on STM32, supporting network communication and multiple input/output interfaces, suitable for access control management systems.

## Hardware Specifications

### Main Controller

- **Model**: STM32F103RET6
- **Core**: ARM Cortex-M3
- **Frequency**: 72MHz
- **Flash**: 512KB
- **SRAM**: 64KB
- **Package**: LQFP64

### Network Interface

- **Ethernet Chip**: W5500
- **Interface**: SPI
- **Speed**: 10/100Mbps
- **Protocol Support**: TCP/IP, UDP

### Output Interfaces

#### Relay Output

- **Quantity**: 2 channels
- **Contact Type**: Normally Open & Normally Closed
- **Load Capacity**: 250VAC/5A or 30VDC/5A
- **Application**: Door lock control, alarm output

#### Buzzer Output

- **Quantity**: 1 channel
- **Application**: Alarm prompt, operation feedback

### Input Interfaces

#### RS485 Interface

- **Quantity**: 3 channels
- **Communication Rate**: Up to 115200bps
- **Isolation**: Optical isolation
- **Application**: Card reader communication, expansion modules

#### Wiegand Interface

- **Quantity**: 2 channels
- **Data Format**: Data0/Data1
- **Application**: Card reader input

#### Door Open Signal Input

- **Quantity**: 2 channels
- **Isolation**: Optical isolation
- **Application**: Exit button

#### Door Magnetic Input

- **Quantity**: 2 channels
- **Isolation**: Optical isolation
- **Application**: Door magnetic status detection

### Debug Interface

- **Type**: UART
- **Level**: TTL (3.3V)
- **Note**: Shared with RS232, TTL level cannot be used after RS232 is soldered

### Storage and Clock

#### FLASH Storage Chip

- **Model**: W25Q64 (8MB)
- **Interface**: SPI
- **Capacity**: 8MB/16MB
- **Erase/Write Cycles**: >100,000 times
- **Data Retention**: >20 years
- **Application**: Firmware storage, data recording

#### EEPROM Storage Chip

- **Model**: AT24C02 (256B) / AT24C04 (512B)
- **Interface**: I2C
- **Capacity**: 256B/512B

#### Real-time Clock Chip

- **Model**: BM8563ESA
- **Interface**: I2C
- **Backup Power**: 3V button battery
- **Leap Year Compensation**: Automatic
- **Application**: Real-time clock, time recording, scheduled tasks

## Project Structure

```
Access_Control_Controller_HW/
├── SCH/                    # Schematic files
│   ├── 主控.SchDoc        # Main control circuit
│   ├── 电源.SchDoc        # Power circuit
│   ├── TCP_IP.SchDoc      # Ethernet circuit
│   ├── 485.SchDoc         # RS485 circuit
│   ├── 继电器.SchDoc      # Relay output circuit
│   ├── 开关量输入.SchDoc  # Digital input circuit
│   ├── 韦根输入输出.SchDoc # Wiegand interface circuit
│   └── 门禁控制器顶层设计.SchDoc # Top-level schematic
├── PCB/                    # PCB files
│   └── 门禁控制器V0.2.PcbDoc
├── LIB/                    # Component libraries
│   ├── KNX网关.SCHLIB     # Schematic library
│   ├── PcbLib1.PcbLib     # PCB package library
│   └── this.SchLib        # Schematic library
└── Project/                # Project files
    ├── 门禁控制器V0.2.PrjPcb
    └── 门禁控制器V0.2.PrjPcbStructure
```

## Power Specifications

- **Input Voltage**: DC 12V -24V
- **Power Protection**: Over-voltage protection, over-current protection, reverse connection protection

## Features

- Support TCP/IP network communication for remote control
- Dual access control, supporting dual door management
- Support multiple card reader interfaces (Wiegand, RS485)
- Real-time door open signal detection
- Status output and alarm functions
- Debug interface for easy development and maintenance
- Optical isolation design for strong anti-interference capability
- External FLASH storage for large capacity data recording
- EEPROM configuration storage, non-volatile
- Real-time clock function for time recording and scheduled tasks

## Development Tools

- **Tool**: Altium Designer

## Notes

1. **Debug Interface Selection**: Debug UART shares the same physical interface with RS232, TTL level cannot be used after RS232 level conversion chip is soldered
2. **Power Connection**: Please confirm the power supply voltage is DC 12V and the polarity is correct before powering on
3. **Relay Load**: Surge absorption circuit is required when relay output is connected to inductive load
4. **RS485 Termination**: 120Ω termination resistors must be added at both ends of RS485 bus
5. **Wiegand Wiring**: Wiegand interface cable length is recommended not to exceed 100 meters

## Version Information

- **Current Version**: V0.2
- **Update Date**: 2026-03-29

## License

This project is for learning and reference only.

## Contact

If you have any questions or suggestions, please provide feedback through project Issues.
