# Diversi-DIAL Debugging Guide

## Apple //e BBS System Debugging and Analysis

This guide provides comprehensive debugging information for Diversi-DIAL Master running on Apple //e hardware, including common issues, diagnostic techniques, and troubleshooting procedures.

## System Startup Debugging

### Initialization Sequence ($1800-$189A)
```
$1800: LDX #$FF ; TXS  - Stack pointer setup
$1803: JSR $189A        - System initialization
$1806: LDX #$02         - Version number setup
```

**Common Issues:**
- **Stack corruption**: Check for TXS instruction execution
- **Memory conflicts**: Verify 64K RAM availability
- **Hardware detection**: Ensure 80-column card presence

### Debug Breakpoints
Set breakpoints at these critical addresses:
- **$1800**: System entry point
- **$189A**: Hardware initialization
- **$28B4**: Main loop entry
- **$224A**: Command processor

## Hardware Interface Debugging

### ACIA Communication Issues

#### Status Register Analysis ($C0n6 for Hayes)
```assembly
LDA $C096    ; Read ACIA status (slot 1)
AND #$08     ; Test RDRF (Receive Data Register Full)
BEQ no_data  ; Branch if no data available
```

**Status Bit Debugging:**
- **Bit 3 (RDRF)**: Data available flag
- **Bit 4 (TDRE)**: Transmit ready flag  
- **Bit 7 (IRQ)**: Interrupt pending

#### Common ACIA Problems
1. **No Data Reception**:
   - Check phone line connection
   - Verify modem carrier detect
   - Test ACIA status register reads
   - Confirm baud rate settings

2. **Garbled Data**:
   - Baud rate mismatch
   - Parity/stop bit configuration
   - Line noise or poor connection
   - ACIA overrun errors

3. **No Transmission**:
   - Check TDRE flag before writing
   - Verify modem ready signals
   - Test ACIA data register writes

### Keyboard Interface Debugging

#### Keyboard Register Monitoring
```assembly
LDA $C000    ; Read keyboard data
BMI key_pressed  ; Branch if bit 7 set
```

**Debug Checks:**
- **$C000 bit 7**: Key pressed indicator
- **$C010 read**: Clears keyboard flag
- **Character codes**: 7-bit ASCII values

## Memory System Debugging

### Zero Page Variable Monitoring
Critical variables to watch:

#### Channel Management ($C0-$C7)
```
$C0: Channel 0 buffer pointer (console)
$C1: Channel 1 buffer pointer (line 1)
...
$C7: Channel 7 buffer pointer (line 7)
```

#### System Status ($D0-$F7)
```
$D0-$D7: Channel status flags
$E0-$E7: User authentication state  
$F0-$F7: Session timing
```

### Memory Banking Issues
Common problems with language card/auxiliary memory:
- **Bank switching**: Verify $C080-$C08F access
- **Data corruption**: Check bank selection logic
- **Email storage**: Test auxiliary memory writes

## Communication Flow Debugging

### Main Loop Analysis ($28B4)
```assembly
$28B4: LDA #$40      ; System status flag
$28B6: CMP $90       ; Compare current status
$28B8: BEQ $28BF     ; Branch if unchanged
```

**Debug Monitoring:**
- **$90**: System status register
- **$A0**: Input buffer status
- **$F2**: Main loop state flag

### Channel Polling Sequence
Track round-robin polling:
1. Check channel status flags ($D0-$D7)
2. Read ACIA status registers
3. Process available data
4. Update channel buffers
5. Advance to next channel

## Command Processing Debugging

### Command Parser ($224A)
```assembly
$224A: LDY #$04      ; Parameter index
$224C: LDA $18,X     ; Channel status  
$224E: BNE error     ; Branch if busy
```

**Debug Points:**
- **Command format**: Check for "/" prefix
- **Channel validation**: Verify channel 0-7 range
- **Parameter parsing**: Track command arguments
- **Access control**: Verify user permissions

### Common Command Issues
1. **Invalid Commands**:
   - Missing "/" prefix
   - Invalid channel numbers
   - Malformed parameters

2. **Permission Errors**:
   - Insufficient access level
   - Channel not authenticated
   - Time limit exceeded

3. **Processing Failures**:
   - Buffer overflow
   - Memory allocation errors
   - Network communication timeouts

## Network and Linking Debugging

### Station Linking Issues
1. **Connection Problems**:
   - Phone line quality
   - Modem compatibility
   - Protocol synchronization

2. **Data Integrity**:
   - Checksum failures
   - Packet loss
   - Timing issues

3. **Authentication**:
   - Station ID verification
   - Password exchange
   - Access permission levels

## Performance Analysis Tools

### CPU Utilization Monitoring
Track time spent in major routines:
- **Main loop**: Should be ~60Hz
- **ACIA polling**: Minimize overhead
- **Command processing**: Efficient parsing
- **Memory operations**: Fast zero-page access

### Memory Usage Analysis
Monitor memory allocation:
- **User buffers**: Per-channel allocation
- **Email storage**: 64K limit tracking
- **System variables**: Zero-page usage
- **Stack depth**: Prevent overflow

## Error Recovery Procedures

### System Restart Sequences
1. **Soft Reset**: Reinitialize variables
2. **Hardware Reset**: Full ACIA reinitialization  
3. **Memory Clear**: Zero critical buffers
4. **User Logout**: Clean channel state

### Data Recovery Methods
1. **Buffer Backup**: Preserve user data
2. **Email Recovery**: Auxiliary memory scan
3. **User Database**: Integrity checking
4. **Log Analysis**: Error pattern detection

## Diagnostic Commands

### Built-in Debug Features
- **/DEBUG**: Enter debug mode (MASTER access)
- **/TRACE**: Enable system tracing
- **/MONITOR<line>**: Watch specific channel
- **/STATS**: System performance metrics

### Manual Debug Techniques
```assembly
; Set breakpoint at main loop
BRK        ; Force debugger entry
NOP        ; Placeholder for patching
```

### Memory Dumps
Critical areas to examine:
- **$0000-$00FF**: Zero page variables
- **$0400-$047F**: Status display line 1
- **$0480-$04FF**: Status display line 2
- **$C090-$C0FF**: ACIA register space

## Common Error Patterns

### Startup Failures
1. **Hardware missing**: 80-column card required
2. **Memory insufficient**: Need 64K minimum
3. **Modem detection**: ACIA not responding
4. **Phone line issues**: No dial tone

### Runtime Errors
1. **Channel lockup**: ACIA not responding
2. **Memory corruption**: Bank switching errors
3. **User timeouts**: Session management
4. **Command failures**: Parser errors

### Network Problems
1. **Link failures**: Connection lost
2. **Data corruption**: Protocol errors
3. **Synchronization**: Timing issues
4. **Authentication**: Security failures

## Testing Procedures

### Hardware Verification
1. **Memory test**: Read/write all banks
2. **ACIA test**: Loop-back verification
3. **Keyboard test**: All key responses
4. **Display test**: Screen memory access

### Software Testing
1. **Command parsing**: All command variations
2. **User management**: Account operations
3. **Email system**: Message handling
4. **Network functions**: Station linking

### Load Testing
1. **Multi-user**: All 7 lines active
2. **Command flood**: Rapid command entry
3. **Memory stress**: Maximum data storage
4. **Network load**: Multiple station links

## Advanced Debugging Techniques

### Assembly-Level Debugging
- **Single stepping**: Instruction-by-instruction
- **Register monitoring**: A, X, Y, flags
- **Memory watching**: Critical addresses
- **Call stack**: Subroutine tracking

### Logic Analyzer Use
For hardware-level debugging:
- **Address bus**: Memory access patterns
- **Data bus**: Read/write operations
- **Control signals**: IRQ, R/W timing
- **Peripheral access**: ACIA communication

This debugging guide provides the tools and knowledge needed to diagnose and resolve issues with Diversi-DIAL Master on Apple //e hardware, from basic startup problems to complex multi-user scenarios.