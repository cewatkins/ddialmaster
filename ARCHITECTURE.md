# Diversi-DIAL Technical Architecture

## System Overview

### Platform Architecture
- **Target Platform**: Apple //e with 64K RAM
- **Memory Layout**: 6502 addressing with specific memory mapping
- **I/O Architecture**: Serial communication via modem cards
- **Real-time Design**: Interrupt-driven multi-line handling

### Core Components
1. **Main Program Loop**: Handles user input and system state
2. **Serial I/O Manager**: Manages multiple modem connections
3. **Command Parser**: Processes user commands and system functions
4. **Memory Manager**: Handles dynamic memory allocation
5. **Network Interface**: Manages inter-station communication

## Memory Architecture

### Memory Map (Apple //e 64K)
```
$0000-$00FF   Zero Page (critical system variables)
$0100-$01FF   Stack Page
$0200-$02FF   DOS/System Buffer Area
$0300-$03FF   Vector and Buffer Area
$0400-$07FF   Text Page 1 (Primary Display)
$0800-$0BFF   Text Page 2 (Auxiliary Display)
$0C00-$1FFF   Free RAM (5K available)
$2000-$3FFF   Hi-Res Graphics Page 1
$4000-$5FFF   Hi-Res Graphics Page 2
$6000-$95FF   DOS and System Area
$9600-$BFFF   Free RAM (10.5K available)
$C000-$CFFF   I/O Space (modem cards)
$D000-$F7FF   DOS/ROM Area
$F800-$FFFF   Monitor ROM
```

### Diversi-DIAL Memory Usage
```
$1800-$2000   Program Start/Initialization Code
$2000-$4000   Main Program Code
$4000-$6000   User Database and Message Buffers
$6000-$8000   Email Storage System
$8000-$9000   Command Processing Tables
$9000-$9600   System Variables and Status
```

### Dynamic Memory Management
- **User Session Data**: Allocated per connected line
- **Message Buffers**: Dynamic allocation for chat/email
- **Command Tables**: Static allocation for efficiency
- **Network Buffers**: Reserved space for inter-station communication

## Serial I/O Architecture

### Modem Interface Design
```
Slot 1-7: Individual modem cards
Each slot provides:
- Data input/output via 6551 ACIA or compatible
- Interrupt capability for async operation
- Status monitoring for carrier detect/ring
```

### I/O Channel Management
```
Channel Structure:
- Line Number (1-7)
- Connection Status (Connected/Disconnected/Ringing)
- User State (Login/Chat/Email/Command)
- Input Buffer (256 bytes per line)
- Output Buffer (256 bytes per line)
- Timeout Counters
```

### Interrupt Handling
- **Serial Interrupts**: Character receive/transmit ready
- **Timer Interrupts**: System clock and user timeouts
- **Carrier Detect**: Connection status monitoring
- **Ring Detect**: Incoming call handling

## Command Processing System

### Command Parser Architecture
```
Input Processing:
1. Character Input → Line Buffer
2. Command Recognition (starts with '/')
3. Parameter Parsing
4. Access Level Validation
5. Command Execution
6. Response Generation
```

### Command Table Structure
```
Command Entry:
- Command String (e.g., "H", "HELP")
- Minimum Access Level (USER/PASSWORD/MASTER)
- Function Pointer
- Parameter Count
- Help Text Pointer
```

### Multi-Level Access Control
- **USER Level**: Basic chat, email, information commands
- **PASSWORD Level**: User management, logs, configuration
- **MASTER Level**: System control, debugging, network management

## Real-Time System Design

### Main Program Loop
```
Main Loop:
1. Check all serial lines for input
2. Process pending commands
3. Handle system maintenance tasks
4. Update display status
5. Process network communications
6. Handle timeouts and cleanup
```

### Interrupt Service Routines
```
Serial ISR:
- Save processor state
- Identify interrupt source
- Buffer incoming character
- Set processing flag
- Restore processor state

Timer ISR:
- Update system clock
- Check user timeouts
- Process periodic tasks
- Update status display
```

### Multi-User State Management
Each connected user maintains:
- **Session State**: Login status, access level, current mode
- **Input State**: Command buffer, parsing state
- **Output State**: Message queue, display formatting
- **Timing State**: Connect time, idle time, limits

## Chat Channel Architecture

### Channel Implementation
```
Channel Structure:
- Channel Number (1-4)
- User List (linked list of connected users)
- Message History (circular buffer)
- Channel Topic/Status
- Access Restrictions
```

### Message Broadcasting
```
Broadcast Algorithm:
1. Receive message from source user
2. Add timestamp and user identification
3. For each channel subscriber:
   - Check user availability
   - Queue message in output buffer
   - Set transmission flag
4. Update message history
```

### Channel Switching
- **User State Tracking**: Remember channel membership
- **Message Routing**: Direct messages to appropriate channels
- **Cross-Channel Commands**: Allow channel management commands

## Email System Architecture

### Email Storage Design
```
Message Structure:
- Message ID (unique identifier)
- From/To User IDs
- Timestamp
- Subject Line (40 characters max)
- Message Body (variable length)
- Status Flags (read/unread/kept/deleted)
```

### Email Database
- **Message Index**: Sorted by timestamp/user
- **User Mailboxes**: Linked lists per user
- **Free Space Management**: Deleted message recovery
- **Storage Limits**: Automatic cleanup of old messages

### 80-Column Card Integration
- **Extended Memory Access**: Use auxiliary memory for email storage
- **Display Management**: Handle 80-column text formatting
- **Memory Banking**: Switch between main and auxiliary memory

## Network Architecture (Multi-Station)

### Inter-Station Communication
```
Network Protocol:
- Station Identification
- Message Routing Headers
- User Database Synchronization
- Command Forwarding
- Status Monitoring
```

### Parallel Card Interface
```
Hardware Interface:
- Interface Two parallel cards (slot 7)
- 16-bit data path via parallel port
- Handshaking protocol for reliability
- Cable connection between stations
```

### Distributed System Design
- **User Database Sync**: Keep user accounts synchronized
- **Message Routing**: Forward messages between stations
- **Load Distribution**: Balance users across stations
- **Fault Tolerance**: Handle link failures gracefully

## Hardware Integration

### Apple //e Specific Features
```
Clock Support:
- Real-time clock card integration
- Automatic time/date display
- User timeout management
- System uptime tracking
```

### Modem Card Compatibility
```
Supported Hardware:
- Novation Apple Cat II (6551 ACIA)
- Hayes Micromodem //e (6551 ACIA)
- Generic 6551-based cards
- Custom initialization strings
```

### Slot Configuration
- **Flexible Slot Assignment**: Any slot 1-7 for modems
- **Automatic Detection**: Probe slots for modem presence
- **Configuration Storage**: Save slot assignments
- **Hot-swap Support**: Add/remove modems without reboot

## Performance Optimization

### Memory Efficiency
- **Shared Code Segments**: Common routines for all users
- **Compact Data Structures**: Minimize memory overhead
- **Buffer Management**: Efficient use of limited RAM
- **Code Overlays**: Swap in specialty functions as needed

### I/O Optimization
- **Interrupt-Driven I/O**: Minimize CPU polling overhead
- **Buffer Prioritization**: Critical messages first
- **Batch Processing**: Group similar operations
- **Lazy Evaluation**: Defer non-critical operations

### Real-Time Responsiveness
- **Predictable Timing**: Bounded response times
- **Priority Scheduling**: Critical operations first
- **Timeout Management**: Prevent system lockup
- **Resource Limits**: Prevent user monopolization

## Security Architecture

### Access Control System
```
Security Levels:
- Anonymous (pre-login)
- USER (basic access)
- PASSWORD (enhanced privileges)
- MASTER (full system control)
```

### Authentication
- **Username/Password**: Simple but effective for 1985
- **Session Management**: Track login state per line
- **Timeout Enforcement**: Automatic logout
- **Account Lockout**: Prevent brute force attacks

### Audit Trail
- **Login/Logout Logging**: Track user sessions
- **Command Logging**: Record significant actions
- **Error Logging**: Track system problems
- **Security Events**: Monitor suspicious activity

## Debugging and Maintenance

### Built-in Diagnostics
```
Debug Commands:
/DEBUG    - Enter debug mode
/TRACE    - Enable system tracing
/DUMP     - Memory dump utilities
/CHECK    - System integrity verification
```

### System Monitoring
- **Real-time Status**: Display system state
- **Performance Metrics**: Track system utilization
- **Error Detection**: Identify problems early
- **Automatic Recovery**: Handle common failures

### Maintenance Features
- **Online Backup**: Save system state while running
- **Hot Configuration**: Change settings without restart
- **User Management**: Add/remove users without downtime
- **Log Rotation**: Manage log file sizes

## Extension Points

### Modular Design
- **Command Extensions**: Add new commands easily
- **Protocol Extensions**: Support new modem types
- **Network Extensions**: Add new link protocols
- **Storage Extensions**: Support additional storage devices

### Configuration Flexibility
- **Runtime Configuration**: Change settings without code changes
- **Site Customization**: Adapt to local requirements
- **Hardware Adaptation**: Support new peripheral cards
- **Protocol Adaptation**: Handle different modem protocols

## Technical Constraints

### Hardware Limitations
- **Memory**: 64K total, fragmented by system needs
- **CPU Speed**: 1MHz 6502, limited processing power
- **I/O Bandwidth**: Serial port limitations
- **Storage**: Limited to floppy/cassette for configuration

### Software Constraints
- **No Virtual Memory**: All code must fit in physical RAM
- **No Protected Mode**: Single address space for all users
- **Limited Stack**: Small stack space per operation
- **No Threads**: Cooperative multitasking only

### Historical Context
- **1985 Technology**: Design reflects era limitations
- **Cost Sensitivity**: Optimize for minimal hardware requirements
- **Reliability**: Must run unattended for hours/days
- **User Expectations**: Match contemporary BBS functionality

This technical architecture document provides comprehensive insight into the sophisticated design of Diversi-DIAL, showcasing advanced programming techniques for the Apple //e platform.