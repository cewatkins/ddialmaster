# Diversi-DIAL Master

A vintage Apple //e telecommunications system for multi-line BBS operations.

## Overview

Diversi-DIAL Master is a sophisticated multi-line BBS (Bulletin Board System) program written for the Apple //e computer, developed by Diversified Software Research in 1985. This system supports up to 7 simultaneous dial-up connections plus a console operator, creating an 8-channel telecommunications hub. The system was commercially licensed for $475 for the first 7 lines, with additional lines costing $50 each.

## Features

- **Multi-Line BBS System**: Supports up to 7 simultaneous dial-up connections plus console
- **Real-Time Chat**: Multi-channel chat system with channels 1-4
- **Email System**: Built-in email with user accounts and message management
- **Password System**: Dual-tier password system (Primary/Secondary PASSWORDs + system passwords)
- **Station Linking**: Link multiple Diversi-DIAL stations across phone lines or direct connections
- **Modem Support**: Compatible with Novation Apple Cat II and Hayes Micromodem //e
- **System Management**: Comprehensive sysop controls and user management
- **Call Tracking**: Automatic call counting and time management
- **Private Messaging**: User-to-user private messaging system
- **System Messages**: Rotating announcement system

## Hardware Requirements

### Minimum System Requirements
- **Computer**: Apple //e (64K required)
- **Memory**: 64K RAM + 80-column card for email functionality
- **Modems**: 1-7 Novation Apple Cat II or Hayes Micromodem //e compatible
- **Phone Lines**: 1-7 dedicated phone lines with "hunt" feature
- **Loading**: Cassette port for program loading (no disk drive required)

### Recommended Configuration
- **Full 7-modem setup** for maximum capacity
- **Zoom ZM-300 modems** (compatible, ~$75 each circa 1985)
- **Basic phone service** (metered, no touch-tone required)
- **Modular phone jacks** for easy modem connection

### Network Expansion
- **Station Linking**: Connect multiple Diversi-DIAL systems
- **PC Pursuit Support**: Long-distance linking via Telenet
- **Internal Links**: Direct computer-to-computer via parallel cards
- **Interface Two Cards**: $39.95 each for direct linking (MicroDimensions)

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

## Documentation

This repository includes comprehensive documentation:

### Core Files
- **[dialmstr.txt](dialmstr.txt)** - Complete 6502 disassembly with detailed comments
- **[FLOWCHART.txt](FLOWCHART.txt)** - ASCII flowchart of program control flow

### User Documentation
- **[USER_GUIDE.md](USER_GUIDE.md)** - Complete guide for end users
- **[COMMANDS.md](COMMANDS.md)** - Comprehensive command reference

### System Administration  
- **[SYSOP.md](SYSOP.md)** - System operator guide and procedures
- **[HARDWARE.md](HARDWARE.md)** - Hardware setup and configuration guide

### Technical Documentation
- **[ARCHITECTURE.md](ARCHITECTURE.md)** - Technical architecture and design
- **[LICENSE.md](LICENSE.md)** - Legal and licensing information

### Original Documentation (Historical)
- **[DIALINST.txt](DIALINST.txt)** - Original installation instructions
- **[ddial.txt](ddial.txt)** - Main user manual  
- **[extended.txt](extended.txt)** - Extended features guide
- **[link.txt](link.txt)** - Station linking instructions
- **[update.txt](update.txt)** - Software update information

## File Structure

```
ddialmaster/
├── README.md           # Project overview and quick start
├── dialmstr.txt        # Complete 6502 disassembly with comments
├── FLOWCHART.txt       # ASCII flowchart of program control flow
├── USER_GUIDE.md       # End user documentation
├── COMMANDS.md         # Command reference guide
├── SYSOP.md           # System operator guide
├── HARDWARE.md        # Hardware setup guide
├── ARCHITECTURE.md    # Technical architecture documentation
├── LICENSE.md         # Legal and licensing information
├── DIALINST.txt       # Original installation instructions
├── ddial.txt          # Original user manual
├── extended.txt       # Original extended features guide
├── link.txt           # Original linking instructions
└── update.txt         # Original update information
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