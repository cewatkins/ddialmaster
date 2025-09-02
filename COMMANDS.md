# Diversi-DIAL Command Reference

## Command Syntax
- Commands start with `/` (forward slash)
- Case insensitive
- Multiple parameters separated by spaces
- Some commands require PASSWORD access level

## User Commands

### Basic Navigation
- **`/H`** - Display help and command list
- **`/Q`** - Quit/logout from system
- **`/T`** - Display current time and date
- **`/?`** - Show available commands (same as /H)

### Chat Commands
- **`/C<message>`** - Send chat message to all users
- **`/P<user><message>`** - Send private message to specific user
- **`/W`** - Who's online (list current users)
- **`/U`** - List all registered users

### Email Commands  
- **`/E`** - Enter email system
- **`/ER`** - Read email messages
- **`/ES`** - Send email message
- **`/ED`** - Delete email messages
- **`/EL`** - List email summary

### Information Commands
- **`/S`** - Display system statistics
- **`/N`** - Show system news/bulletins
- **`/I`** - Display system information
- **`/V`** - Show software version

## PASSWORD User Commands

### User Management
- **`/A<username><password>`** - Add new user account
- **`/D<username>`** - Delete user account
- **`/L`** - List all user accounts with details
- **`/M<username>`** - Modify user account settings

### System Control
- **`/X`** - Exit to Apple DOS (system maintenance)
- **`/R`** - Reboot system (warm restart)
- **`/K<line>`** - Kick user off specified line
- **`/F`** - Force system maintenance mode

### Log Management
- **`/LG`** - Display system log entries
- **`/LC`** - Clear system logs
- **`/LS`** - Save logs to disk
- **`/LP`** - Print logs (if printer attached)

### Configuration
- **`/CF`** - Configure system settings
- **`/CM`** - Configure modem settings
- **`/CT`** - Set system time and date
- **`/CN`** - Configure network linking

## MASTER User Commands

### Advanced System Control
- **`/DEBUG`** - Enter debug mode
- **`/TRACE`** - Enable system tracing
- **`/DUMP`** - Memory dump utilities
- **`/PATCH`** - Live system patching

### Network Administration
- **`/LINK`** - Manage station links
- **`/ROUTE`** - Configure message routing
- **`/SYNC`** - Synchronize linked stations
- **`/NET`** - Network diagnostic tools

### Maintenance Commands
- **`/BACKUP`** - System backup utilities
- **`/RESTORE`** - System restore functions
- **`/OPTIMIZE`** - System optimization routines
- **`/CHECK`** - System integrity checks

## Email System Commands (Within `/E` mode)

### Reading Messages
- **`R`** - Read next message
- **`R<number>`** - Read specific message number
- **`L`** - List message headers
- **`F`** - Read first message
- **`N`** - Read next message
- **`P`** - Read previous message

### Sending Messages
- **`S`** - Send new message
- **`S<username>`** - Send message to specific user
- **`R<number>`** - Reply to message number
- **`F<number>`** - Forward message

### Message Management
- **`D`** - Delete current message
- **`D<number>`** - Delete specific message
- **`U`** - Undelete last deleted message
- **`K`** - Keep message (prevent auto-deletion)
- **`E`** - Edit draft message

### Email Navigation
- **`Q`** - Quit email system
- **`H`** - Help (email commands)
- **`?`** - Show email help

## Chat Channel Commands

### Channel Management
- **`/J<channel>`** - Join specific chat channel (1-4)
- **`/CH<channel>`** - Change to different channel
- **`/CL`** - List active channels
- **`/CA`** - List all channels with user counts

### Channel Communication
- **`/CB<message>`** - Broadcast to all channels
- **`/CC<channel><message>`** - Send message to specific channel
- **`/CW<channel>`** - Who's in specific channel
- **`/CT<channel><topic>`** - Set channel topic (PASSWORD users)

## System Operator Commands

### User Session Control
- **`/MONITOR<line>`** - Monitor specific line activity
- **`/WALL<message>`** - Send message to all users
- **`/SHUTDOWN<minutes>`** - Schedule system shutdown
- **`/LOCKOUT`** - Lock out non-PASSWORD users

### Security Commands
- **`/BAN<username>`** - Ban user account
- **`/UNBAN<username>`** - Remove user ban
- **`/TRACE<username>`** - Trace user activity
- **`/AUDIT`** - Generate security audit report

### System Statistics
- **`/STATS`** - Detailed system statistics
- **`/USAGE`** - System usage reports
- **`/PEAK`** - Peak usage analysis
- **`/REPORT`** - Generate operational reports

## Network Linking Commands

### Inter-Station Communication
- **`/SEND<station><message>`** - Send message to linked station
- **`/ROUTE<station><command>`** - Execute command on remote station
- **`/STATUS<station>`** - Check linked station status
- **`/PING<station>`** - Test link to station

### Link Management
- **`/CONNECT<station>`** - Establish station link
- **`/DISCONNECT<station>`** - Break station link
- **`/AUTO<station><ON|OFF>`** - Configure automatic linking
- **`/SYNC<station>`** - Synchronize user databases

## Command Categories by Access Level

### ALL USERS
```
/H, /Q, /T, /?, /C, /P, /W, /U, /E, /S, /N, /I, /V
Chat channels: /J, /CH, /CL, /CA, /CB, /CC, /CW
Email: All /E mode commands
```

### PASSWORD USERS
```
All user commands plus:
/A, /D, /L, /M, /X, /R, /K, /F, /LG, /LC, /LS, /LP
/CF, /CM, /CT, /CN
Channel management: /CT
```

### MASTER USERS
```
All PASSWORD commands plus:
/DEBUG, /TRACE, /DUMP, /PATCH
/LINK, /ROUTE, /SYNC, /NET
/BACKUP, /RESTORE, /OPTIMIZE, /CHECK
/MONITOR, /WALL, /SHUTDOWN, /LOCKOUT
/BAN, /UNBAN, /AUDIT
/STATS, /USAGE, /PEAK, /REPORT
Network: /SEND, /ROUTE, /STATUS, /PING, /CONNECT, /DISCONNECT, /AUTO
```

## Command Parameters

### User Specification
- **`<username>`** - Exact username (case insensitive)
- **`<line>`** - Line number (1-7)
- **`<channel>`** - Channel number (1-4)

### Message Format
- **`<message>`** - Text message (up to 255 characters)
- **`<topic>`** - Channel topic (up to 40 characters)

### System Parameters
- **`<minutes>`** - Time value in minutes
- **`<station>`** - Linked station identifier
- **`<number>`** - Message or reference number

## Error Messages

### Access Denied
- **"COMMAND NOT AVAILABLE"** - Insufficient access level
- **"PASSWORD REQUIRED"** - Need PASSWORD status
- **"MASTER ACCESS ONLY"** - MASTER level required

### Parameter Errors
- **"INVALID USER"** - Username not found
- **"INVALID LINE"** - Line number out of range
- **"INVALID CHANNEL"** - Channel number invalid
- **"USER NOT ONLINE"** - Target user not connected

### System Errors
- **"SYSTEM BUSY"** - Command temporarily unavailable
- **"LINK DOWN"** - Network connection failed
- **"DISK ERROR"** - Storage system problem
- **"MEMORY FULL"** - Insufficient system memory

## Command Aliases

### Common Shortcuts
- **`/Q`** = `/QUIT`
- **`/H`** = `/HELP`
- **`/W`** = `/WHO`
- **`/T`** = `/TIME`

### Email Shortcuts
- **`/ER`** = `/EMAIL READ`
- **`/ES`** = `/EMAIL SEND`
- **`/ED`** = `/EMAIL DELETE`

## Usage Examples

### Basic User Session
```
/W              (see who's online)
/C Hello all!   (send chat message)
/E              (enter email)
  L             (list messages)
  R 1           (read message 1)
  Q             (quit email)
/Q              (logout)
```

### PASSWORD User Tasks
```
/A newuser pass123    (add user)
/L                    (list users)
/LG                   (view logs)
/K 3                  (kick line 3)
```

### System Administration
```
/STATS                (system stats)
/MONITOR 1            (monitor line 1)
/WALL System maintenance in 5 minutes
/SHUTDOWN 5           (shutdown in 5 min)
```

This command reference provides comprehensive documentation for all Diversi-DIAL commands across all user access levels.