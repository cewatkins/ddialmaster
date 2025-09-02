# Diversi-DIAL User Guide

## Getting Started

### Connecting to the System
1. **Dial the BBS number** with your modem
2. **Wait for connection** (you'll hear modem handshake tones)
3. **Press ENTER** when you see the connect message
4. **Follow the login prompts**

### First Time Users
```
Welcome to Diversi-DIAL!

First time caller? (Y/N): Y
Enter your name: [Your Name]
Choose a username: [username]
Choose a password: [password]
Verify password: [password]
```

### Returning Users
```
Username: [your username]
Password: [your password]
```

## System Overview

### What is Diversi-DIAL?
Diversi-DIAL is a multi-line chat and email system that allows multiple users to connect simultaneously for real-time communication. Think of it as an early social network where you can:
- Chat with other users in real-time
- Send and receive private email messages
- Participate in group discussions
- Access system information and news

### System Features
- **Real-time Chat**: Talk with up to 28 users at once (4 channels × 7 lines)
- **Private Email**: Send personal messages to other users
- **Multiple Channels**: Join different chat rooms (channels 1-4)
- **User Directory**: Find and connect with other users
- **System News**: Read announcements and updates

## Basic Commands

### Getting Help
- **`/H`** or **`/?`** - Show available commands
- **Type `/H` anytime** you need to see what commands you can use

### Essential Commands
```
/H      - Help (show commands)
/Q      - Quit (logout)
/T      - Time (show current date/time)
/W      - Who (see who's online)
/S      - Statistics (system info)
/N      - News (read bulletins)
```

### Command Format
- **All commands start with `/`** (forward slash)
- **Commands are not case sensitive** (`/h` same as `/H`)
- **Some commands need additional information** (`/C Hello everyone!`)

## Real-Time Chat

### Basic Chat Commands
```
/C<message>     - Send message to everyone
/P<user><msg>   - Send private message to specific user
/W              - See who's online
/U              - List all registered users
```

### Chat Examples
```
/C Hello everyone!           - Send "Hello everyone!" to all users
/P john Hi there!           - Send "Hi there!" privately to user "john"
/C Anyone want to chat?     - Ask if anyone wants to talk
```

### Chat Etiquette
1. **Be polite and respectful** to other users
2. **Don't monopolize the conversation** - let others talk
3. **Use private messages** for personal conversations
4. **Keep messages appropriate** for all audiences
5. **Don't use all CAPS** - it's considered shouting

## Chat Channels

### Understanding Channels
The system has 4 chat channels (1-4), like different chat rooms. Each channel can hold users from all connected lines.

### Channel Commands
```
/J<channel>     - Join specific channel (1-4)
/CH<channel>    - Change to different channel
/CL             - List active channels
/CA             - Show all channels with user counts
/CB<message>    - Broadcast to all channels
/CC<ch><msg>    - Send message to specific channel
/CW<channel>    - See who's in specific channel
```

### Channel Examples
```
/J1             - Join channel 1
/CC2 Hello!     - Send "Hello!" to channel 2
/CW3            - See who's in channel 3
/CB Testing     - Send "Testing" to all channels
```

### Using Channels Effectively
- **Channel 1**: Usually the main/general chat
- **Channel 2**: Often used for specific topics
- **Channel 3**: May be for games or special events
- **Channel 4**: Sometimes reserved for private groups

## Email System

### Accessing Email
- **Type `/E`** to enter the email system
- **You'll see a different prompt** when in email mode
- **Type `H` for email help** (no slash needed in email mode)

### Reading Email
```
Enter Email Mode: /E

Email Commands:
L       - List message headers
R       - Read next message
R<num>  - Read specific message number
F       - Read first message
N       - Read next message
P       - Read previous message
Q       - Quit email system
```

### Sending Email
```
S           - Send new message
S<username> - Send message to specific user
R<number>   - Reply to message number
```

### Email Example Session
```
/E              (enter email)
L               (list messages)
R 1             (read message 1)
S john          (send message to john)
  [type your message]
  [press CTRL-Z or type /END to finish]
Q               (quit email)
```

### Email Tips
1. **Check email regularly** - messages may have time limits
2. **Delete old messages** to save space
3. **Use descriptive subjects** when sending messages
4. **Reply promptly** to important messages

## System Information

### Useful Information Commands
```
/S      - System statistics (users, calls, uptime)
/N      - News and announcements
/I      - System information
/V      - Software version
/T      - Current time and date
```

### Understanding the Display

#### Top Status Lines
The top 2 lines of your screen show system status:
```
Line 1: [CUTOFF][1234567][TIME][STATUS]
Line 2: [CHANNELS][CALLS][DATE/TIME]
```

#### What the Status Means
- **Numbers 1234567**: Show which lines have users connected
- **Time Limit**: How many minutes you have left (if you're not a PASSWORD user)
- **Call Counts**: Number of calls today and in the last 24 hours
- **Channels**: Shows activity in chat channels 1-4

## User Accounts and Access Levels

### Account Types
1. **Standard Users**: Can chat, send email, use basic commands
2. **PASSWORD Users**: Have additional privileges and longer time limits
3. **MASTER Users**: System operators with full access

### Time Limits
- **Standard users** may have time limits (shown in status display)
- **PASSWORD users** typically have unlimited time
- **System may lock out standard users** during busy periods

### Getting PASSWORD Status
- **Ask the system operator** (SysOp) for PASSWORD privileges
- **Demonstrate you're a regular, helpful user**
- **Follow system rules and be respectful**

## Tips for New Users

### Making Friends
1. **Be friendly** in your first messages
2. **Introduce yourself** when you join conversations
3. **Ask questions** - experienced users are usually helpful
4. **Participate in discussions** - don't just lurk
5. **Be patient** - it may take time to feel comfortable

### System Etiquette
1. **Read the news** (`/N`) for important announcements
2. **Don't spam** with repeated messages
3. **Respect other users' privacy**
4. **Follow the Golden Rule** - treat others as you'd like to be treated
5. **When in doubt, ask** - use `/P sysop <question>`

### Technical Tips
1. **Your connection may be slow** - be patient
2. **Press ENTER** if the system seems stuck
3. **Use `/Q` to logout properly** - don't just hang up
4. **Check your time limit** regularly (shown at top of screen)
5. **Save important email messages** - they may be deleted automatically

## Common Problems and Solutions

### Connection Issues
**Problem**: Can't connect or get disconnected
**Solutions**:
- Check your modem settings
- Try calling back - lines may be busy
- Verify the phone number
- Check your phone line

### Login Problems
**Problem**: Can't login or password doesn't work
**Solutions**:
- Make sure CAPS LOCK is off
- Type username and password exactly as registered
- Contact the SysOp for password reset
- You may need to re-register

### Command Problems
**Problem**: Commands don't work
**Solutions**:
- Make sure you start commands with `/`
- Check spelling and spacing
- Use `/H` to see available commands
- Some commands may require higher access level

### Chat Problems
**Problem**: Nobody responds to chat messages
**Solutions**:
- Check if anyone is online (`/W`)
- Try different channels (`/J2`, `/J3`, `/J4`)
- Be patient - users may be busy
- Try at different times when more users are online

## Advanced Features

### Private Conversations
Use private messages for personal discussions:
```
/P username I wanted to ask you about...
/P username Thanks for the help earlier!
```

### Channel Management
Switch between channels to find active conversations:
```
/CL             (see which channels are active)
/J2             (join channel 2)
/CW2            (see who's in channel 2)
```

### Email Management
Organize your email effectively:
```
/E              (enter email)
L               (list all messages)
D 3             (delete message 3)
K 5             (keep message 5 from auto-deletion)
```

## System Limitations

### Technical Constraints
- **Maximum 7 phone lines** (maximum 7 simultaneous users)
- **4 chat channels** available
- **Email storage is limited** - delete old messages
- **System may have time limits** for standard users

### Respectful Usage
- **Don't tie up the system** unnecessarily
- **Logout when you're done** (`/Q`)
- **Be considerate** of other users waiting to connect
- **Follow system rules** posted in news

## Getting More Involved

### Becoming a Regular User
1. **Visit regularly** to become part of the community
2. **Help new users** learn the system
3. **Participate in discussions** and events
4. **Follow system guidelines** consistently
5. **Ask about PASSWORD status** once you're established

### Contributing to the Community
- **Share interesting topics** for discussion
- **Help moderate conversations** to keep them friendly
- **Report problems** to the SysOp
- **Suggest improvements** for the system
- **Welcome new users** and help them learn

## Contact Information

### Getting Help
- **Online Help**: Type `/H` for commands
- **Private Message SysOp**: `/P sysop <your question>`
- **Email SysOp**: Use `/E` to send email to system operator
- **Check News**: `/N` for announcements and updates

### System Rules
Most systems will have specific rules posted in the news section. Always read these with `/N` and follow them to maintain your account in good standing.

Remember: Diversi-DIAL is a community. The more you contribute positively, the more you'll enjoy your time on the system. Be patient, be kind, and have fun exploring this early form of social networking!