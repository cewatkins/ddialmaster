# Diversi-DIAL Hardware Setup Guide

## System Requirements

### Computer System
- **Required**: Apple //e with 64K RAM
- **Clock Support**: Apple //e required for proper timekeeping
- **Compatibility**: Apple II+ and //c can run demo version but clock won't keep correct time
- **80-Column Card**: Required for email functionality (64K extended 80-column card)

### Modem Configuration

#### Supported Modems
1. **Novation Apple Cat II** (Original compatibility)
2. **Hayes Micromodem //e** (Standard compatibility)
3. **Zoom ZM-300** (Recommended, ~$75 circa 1985)
4. **Transend Corporation Micromodem //e Compatible** (Recommended)
   - List Price: $79
   - Dealer pricing available for 5+ modems
   - Contact: Brett Clippard at Transend (415) 851-3402

#### Modem Installation
- **Slots 1-7**: One modem per slot (up to 7 modems maximum)
- **Slot Assignment**: Use Diversi-DIAL modem configuration program (Option #9)
- **Warning**: Incorrect slot configuration can damage disk drives
- **Default**: Program ships with no modems configured (safe to run)

### Phone Line Setup

#### Basic Service
- **Type**: Most basic phone service (metered service recommended)
- **Features**: No touch-tone required (basic rotary service adequate)
- **Lines**: 1-7 dedicated incoming lines
- **Hunt Feature**: Essential - routes calls to next available line when busy

#### Installation Costs (1985 pricing)
- **Installation**: ~$22 per line
- **Monthly Service**: ~$16.50 per line
- **Connection**: 7 modular jacks recommended for easy setup

#### Wiring Options
1. **Phone Company Installation**: 7 modular jacks
2. **Self-Installation**: Custom cabling to save installation costs
3. **Modular Cords**: Included with modems, plug directly into jacks

### Program Loading System

#### Cassette Port Loading
- **Interface**: Uses Apple //e cassette port
- **Advantages**:
  - Saves a slot (no disk controller needed)
  - Avoids disk drive cost
  - Only need to load once
- **Load Time**: Approximately 4 minutes
- **Media**: Audio cassette tape

#### Alternative Loading (Two-Computer Setup)
- **Method**: Cable from cassette-out to cassette-in
- **Modification Required**: Cut resistor R9 (Apple //e) or R18 (Apple II+)
- **Resistor**: 100 ohm (brown-black-brown)
- **Procedure**: Cut one side and lift slightly

### System Expansion Options

#### Station Linking Hardware

##### Long-Distance Linking (PC Pursuit)
- **Service**: PC Pursuit by Telenet
- **Cost**: $25/month flat rate (unlimited connection time)
- **Coverage**: 14 major cities (as of 1985)
- **Signup**: 800-368-4215 (voice) or 800-835-3001 (BBS)
- **Requirements**: Local Telenet node access

##### Direct Computer Linking
- **Hardware**: Interface Two parallel cards
- **Supplier**: MicroDimensions, Inc. (1-800-423-7252)
- **Cost**: $39.95 per card
- **Cable**: Included with 2-card purchase
- **Installation**: Slot #7 on each computer
- **Connection**: 16-pin DIP sockets (A and B)

#### Multi-Computer Expansion
- **Method**: Connect additional computers via parallel cards
- **Capacity**: Unlimited expansion possible
- **Configuration**: 
  - Main computer: Slot #7 (A socket), Slot #6 (B socket)
  - Additional computers: Slot #7 (A socket only)
- **Restrictions**: Never connect B-to-B (electrically incompatible)

### Screen Display Layout

#### Status Display (Top 2 Lines)
```
Line 1: [CUTOFF][1234567][TIME_LIMIT][-][CALLER_TIMES][STATUS_CHARS]
Line 2: [CHANNELS][STATUS][CALL_COUNT][24HR_COUNT][DATE/TIME]
```

#### Status Indicators
- **Cutoff Time**: Upper left (3 = 30-minute cutoff)
- **Caller Numbers**: 1234567 (line assignments)
- **Channel Display**: 1-4 (* = offline)
- **Time Limit**: Minutes for non-PASSWORD users
- **Lock Indicator**: Inverse "-" when non-PASSWORD users locked out
- **Connection Times**: Time since signon for each caller
- **Login Status**: "!" during signon, "+/*/<space>" for PASSWORD type
- **System Status**: "." after reboot, inverse "G" after /LG, blank otherwise
- **Call Counters**: Calls since midnight, previous 24-hour total
- **Date/Time**: Current system date and time

### Electrical Specifications

#### Power Requirements
- **Standard Apple //e power supply**
- **Additional draw per modem**: Varies by modem type
- **Cooling**: Ensure adequate ventilation for continuous operation

#### Signal Levels
- **Cassette Input**: Modified output level required for computer-to-computer loading
- **Serial Communication**: Standard RS-232 levels
- **Parallel Linking**: TTL levels via Interface Two cards

### Maintenance and Support

#### Regular Maintenance
- **Daily**: Monitor call logs and system status
- **Weekly**: Check modem connections and phone line status
- **Monthly**: Review user accounts and system performance

#### Troubleshooting
- **Modem Issues**: Check slot configuration and physical connections
- **Phone Line Problems**: Verify hunt group setup with phone company
- **Loading Issues**: Check cassette connections and audio levels
- **Link Problems**: Verify cable connections and card configurations

#### Support Contacts (Historical)
- **Diversified Software Research**: Original developer
- **Transend Corporation**: (415) 851-3402 for modems
- **MicroDimensions, Inc**: 1-800-423-7252 for parallel cards
- **Phone Company**: Local service for hunt group setup

### Economic Considerations (1985)

#### Initial Investment
- **Software License**: $475 (first 7 lines)
- **Apple //e Computer**: ~$700
- **7 Modems**: ~$525 ($75 each)
- **Phone Installation**: ~$154 (7 lines × $22)
- **Total Hardware**: ~$1,854

#### Monthly Operating Costs
- **Phone Service**: ~$115.50 (7 lines × $16.50)
- **PC Pursuit**: $25 (if using long-distance linking)
- **Electricity**: Minimal (Apple //e + modems)

#### Revenue Potential
- **Subscription Fees**: User-defined pricing
- **Message Services**: Premium features
- **Network Linking**: Multi-station operations

### Configuration Recommendations

#### Startup Configuration
1. **Begin with 1-2 modems** to test system
2. **Expand gradually** as user base grows
3. **Configure hunt group** before adding multiple lines
4. **Test modem compatibility** before bulk purchase
5. **Plan for expansion** from initial installation

#### Production Setup
1. **Full 7-modem configuration** for maximum capacity
2. **Reliable UPS system** for power protection
3. **Dedicated phone lines** (no shared voice/data)
4. **Proper ventilation** for continuous operation
5. **Backup system** for maintenance windows

This hardware setup guide provides the foundation for establishing a professional Diversi-DIAL BBS operation as originally intended by the software designers.