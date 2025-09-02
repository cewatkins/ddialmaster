# Divers-Dial Master

A vintage 6502 assembly telecommunications system for multi-channel dial-up communications.

## Overview

Divers-Dial Master is a sophisticated telecommunications program written for the 6502 microprocessor, likely developed in the 1980s for BBS (Bulletin Board System) or modem pool operations. The system supports multi-channel communication handling with up to 8 simultaneous connections.

## Features

- **Multi-Channel Support**: Handles up to 8 simultaneous communication channels (0-7)
- **UART Interface**: Serial communication through UART registers at $9001
- **Command Processing**: Comprehensive command parser with single-letter commands
- **Screen Management**: Display handling with screen memory at $0400-$04xx
- **Buffer Management**: Sophisticated input/output buffering system
- **Memory Management**: Dynamic memory allocation and pointer management
- **System Configuration**: Configurable system parameters and channel settings

## System Architecture

### Memory Map
- `$0400-$04xx`: Screen/display memory
- `$0100-$01xx`: Stack page (cleared during initialization)
- `$1800-$xxxx`: Main program code
- `$1A00-$xxxx`: String/message data storage
- `$7Fxx-$7Fxx`: System status tables and buffers
- `$9001`: UART data/status register
- `$xxD0-$xxF3`: Data copying range during initialization

### Core Components

1. **Initialization System** (`$1800-$195B`)
   - Stack pointer setup
   - Memory clearing and configuration
   - Channel initialization
   - Screen setup
   - System parameter loading

2. **Communication Handler** (`$1853-$1897`)
   - Serial I/O processing
   - UART interface management
   - Data transmission/reception
   - Channel status monitoring

3. **Main Program Loop** (`$28B4-$2Axx`)
   - Input processing
   - Command dispatching
   - System state management
   - Buffer handling

4. **Command Processor** (`$224A-$23xx`)
   - Command parsing and validation
   - Channel-specific operations
   - System control functions

## Command Structure

Commands follow the format: `#<channel><command>`

Where:
- `#` is the command prefix
- `<channel>` is a digit 0-9 (channels 0-7 are valid)
- `<command>` is a single letter command

### Supported Commands

| Command | Description | Function |
|---------|-------------|----------|
| `M` | Message/Mode | Configure channel messaging mode |
| `O` | Open/Online | Open channel for communication |
| `A` | Answer | Answer incoming connection |
| `L` | Line/Link | Manage line connection status |
| `F` | Flip/Flag | Toggle channel flags |
| `B` | Break/Busy | Set channel to busy/break state |
| `E` | End/Exit | End channel session |
| `X` | eXchange | Exchange/transfer data |
| `C` | Connect/Channel | Connect to specific channel |
| `T` | Terminal/Talk | Enter terminal/talk mode |

### Example Commands
```
#1M    - Set channel 1 to message mode
#3O    - Open channel 3 for communication
#5A    - Answer on channel 5
#2T    - Enter terminal mode on channel 2
```

## Technical Specifications

- **Processor**: 6502 microprocessor
- **Channels**: 8 simultaneous communication channels
- **Memory**: Approximately 32KB program space
- **I/O**: UART-based serial communication
- **Display**: Text-mode screen interface
- **Commands**: 10 primary command types

## File Structure

```
ddialmaster/
├── README.md           # This file
├── dialmstr.txt        # Complete 6502 disassembly with comments
└── docs/              # Additional documentation (if available)
```

## Installation and Usage

This is historical software intended for:
- **Emulation**: Use with 6502 emulators or vintage computer systems
- **Analysis**: Study of early telecommunications software architecture
- **Preservation**: Digital archaeology and computing history

### For Emulation
1. Load the assembled binary at address `$1800`
2. Set reset vector to point to `$1800`
3. Configure UART at `$9001` for serial communication
4. Execute from `$1800` to start the system

### For Assembly
The source would need to be reconstructed from the disassembly and assembled with a 6502 assembler such as:
- CA65 (cc65 suite)
- DASM
- ACME
- xa65

## Development History

Based on the code analysis:
- **Era**: Likely developed in the 1980s
- **Purpose**: Professional telecommunications/BBS system
- **Sophistication**: Advanced for its time with multi-channel support
- **Platform**: Generic 6502 system with UART capability

## Code Quality and Features

The code demonstrates several advanced programming techniques for the 6502:

- **Self-modifying code**: Dynamic address patching for efficiency
- **Indirect addressing**: Sophisticated pointer manipulation
- **Multi-tasking simulation**: Channel switching and state management
- **Error handling**: Command validation and error recovery
- **Modular design**: Clear separation of concerns between subsystems

## Historical Significance

This software represents an important piece of early telecommunications infrastructure:

- **Pre-Internet Networking**: Before widespread Internet adoption
- **BBS Culture**: Part of the bulletin board system ecosystem
- **Microcomputer Communications**: Advanced use of 6502 systems
- **Software Engineering**: Sophisticated system design for limited hardware

## Contributing

This is a historical preservation project. Contributions welcomed for:
- Additional documentation and analysis
- Historical context and background information
- Emulation setup guides
- Source code reconstruction

## License

The original software license is unknown. This repository contains disassembled code for:
- Educational purposes
- Historical preservation
- Technical analysis

If you are the original author or copyright holder, please contact the maintainer.

## Technical Notes

### Memory Layout Details
- Zero page variables extensively used for efficiency
- Channel data structures maintain state per connection
- System tables track active channels and their status
- Buffer management prevents overflow conditions

### Communication Protocol
- UART-based serial communication
- Character-oriented command processing
- Status flags for connection management
- Buffer flow control mechanisms

### System Requirements (Original)
- 6502 or compatible processor
- Minimum 32KB RAM
- UART or serial interface
- Text display capability
- Input device (keyboard/terminal)

---

*This analysis was generated through disassembly examination and may contain interpretations. Original documentation would provide definitive specifications.*